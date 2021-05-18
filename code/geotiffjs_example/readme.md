Accessing ARD over HTTP using geotiff.js
========================================

The Sentinel 1 and 2 ARD are stored in [CEDA](https://archive.ceda.ac.uk/) in [COG](https://www.cogeo.org/) format, which allows you to use HTTP range requests to retrieve data for just the areas/bands you need instead of downloading the whole file. CEDA have very kindly implemented an allow all CORS policy which means you can now do this entirely from a browser.

This example shows the process of creating true colour Sentinel 2 thumbnails using ARD hosted in CEDA, generated entirely within the browser. [`geotiff.js`](https://geotiffjs.github.io/) is used to handle the HTTP range requests to enable us to retrieve data just for our area of interest (within an ARD file) and our bands of interest.

We've created a very basic example in a self contained `index.html` file which can be found alongside this readme. Simply open it in a web browser to see it running (open dev tools to see logs in the console).

Preparing geotiff files for HTTP range requests
-----------------------------------------------
If you're only intending to use the ARD in CEDA, you can skip this section. If you want to host your own data, you'll need to ensure your files are in COG (Cloud Optimised Geotiff) format. HTTP range requests will still work with non-COG files but more (if not all) of the file will be downloaded so it'll be less efficient.

It's also a good idea to add some more overviews while you're at it:

    gdaladdo -r nearest inputfile.tif 2 4 8 16 32 64 128 256 512

Then to process to COG with GDAL 3.1+ (more details on the [cogeo.org](https://www.cogeo.org/developers-guide.html) site):

    gdal_translate -of "COG" -co "COMPRESS=DEFLATE" -co "BIGTIFF=YES" inputfile.tif outputfile.tif

To validate it, you can use the [`validate_cloud_optimized_geotiff.py`](https://github.com/OSGeo/gdal/blob/master/gdal/swig/python/gdal-utils/osgeo_utils/samples/validate_cloud_optimized_geotiff.py) script:

    python validate_cloud_optimized_geotiff.py outputfile.tif

| Note that the script has been updated for GDAL 3.1+. If you have an older copy saved somewhere, you'll want to update it.

When hosting the files, you'll want to check that your server supports byte-range requests, and if you plan to send the requests from the client side, then you may also need to configure [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS).

Using geotiff.js to retrieve chunks of data
-------------------------------------------
For full documentation, refer to the [geotiff.js site](https://geotiffjs.github.io/).

`geotiff.js` is a very handy Javascript library which can be used to read raw data from geotiff files. In this case we're using it to read data remotely from the CEDA archive, letting it handle the logic of range requests.

First set up the data source and get the image object (there might be multiple images in a file). 

    let tiff = await GeoTIFF.fromUrl(url);
    let image = await tiff.getImage();

Then get the raster data. Here we're giving a pixel window which is a subset of the whole image, and a list of samples/bands.

    let data = await image.readRasters({ 
        window: pixelBbox,
        samples: [2, 1, 0]
    });

The example included in `index.html` also shows the calculations for converting an OSGB bounding box to a pixel bounding box.

Visualising the data as a true colour thumbnail
-----------------------------------------------
The returned `data` data structure includes the red, green, and blue band pixel level values, in top left to bottom right order. I.e. `data[0][0]` is the red value of the first pixel, `data[1][0]` is the green value of the first pixel, and so on. We also know the width and height of the thumbnail, so we have everything we need to draw a pixel by pixel image.

We can do this using the HTML Canvas element.

    let canvas = document.createElement('canvas')
    canvas.width = thumbnailPixelWidth
    canvas.height = thumbnailPixelHeight

    let ctx = canvas.getContext("2d")

To draw a pixel to the canvas, first set the colour using the retrieved rgb values, and then draw it as a 1px by 1px rectangle at the required location. E.g. for the first pixel

    ctx.fillStyle = `rgb(${data[0][0]}, ${data[1][0]}, ${data[2][0]}, 1)`
    ctx.fillRect(0, 0, 1, 1)

| The last argument in rgb() is the alpha value, which can be set to 0 for no data values.

Then it's just a case of looping to do this for the rest of the pixels (you can see this done in the `index.html` file).

Finally, you may want to return the thumbnail as a data URL so that you can pass it to an image element, and so handle it as a standard image instead of a canvas element.

    let imageElement = new Image(thumbnailPixelWidth, thumbnailPixelHeight)
    imageElement.src = canvas.toDataURL("image/png")
