# Sentinel-1 & Sentinel-2 ARD code list



![logos](images/Logos_updated.png)  


A curated list supporting the use of Sentinel-1 and Sentinel-2 analysis-ready data (ARD) in the UK

---

# Project Background
[JNCC](https://jncc.gov.uk/) are leading a project to help people use [Sentinel-1](https://sentinel.esa.int/web/sentinel/missions/sentinel-1) and [Sentinel-2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2) analysis-ready data ([ARD](https://jncc.gov.uk/our-work/simple-ard-service-faqs/)) provided by the [Defra EO Data Service](https://defradigital.blog.gov.uk/2020/06/18/making-it-easier-to-access-and-use-earth-observation-data/) and the [CEDA Archive](http://archive.ceda.ac.uk/), with a particular focus on accessing data via API (application programming interfaces).  As part of this project, we have set up a public repository for sharing code in any language for processing or analysing Sentinel-1 and Sentinel-2 ARD.  We conducted a survey in July 2020 to gain a better understanding of user needs and inform the choice of code-sharing platform.  Based on the survey results and subsequent discussion with the project team and partners, there is consensus that the best option was to set up this curated list on GitHub.

This project is funded by the Caroline Herschel Framework Partnership Agreement on [Copernicus User Uptake](https://jncc.gov.uk/our-work/copernicus-project/). 

---

# Contents

|   [<b>Tutorials and functions</b>](#tutorials-and-functions )   | <br>

|   [<b>Marine and Coastal Applications</b>](#marine-and-coastal-applications)   |   [Seagrass monitoring](#seagrass-monitoring)   |   [Satellite-derived bathymetry](#satellite-derived-bathymetry)   | <br>

|   [<b>Terrestrial Applications</b>](#terrestrial-applications)   |   [Habitat Change Detection](#habitat-change-detection)   |   [Peatland Mapping](#peatland-mapping)   |   [Upland mapping](#upland-mapping)   |  [habitat mapping](#habitat-mapping)   |
   
|   [GitHub accounts of relevant organisations](#GitHub-accounts-of-relevant-organisations)   |   [Other useful Earth Observation GitHub links](#other-useful-earth-observation-github-links)   |           

<b>Start Here</b>

## Tutorials and functions 
- Introduction to EODS API and creating a simple query. `Python` `Defra` `EODS-API`
- Generate a list of S2 granules with least cloud per granule per orbit for a given date range and geographic area. `Python` `Defra` `EODS-API`
- Clip raster, select single band from raster, re-project raster, create points from raster, and generate zonal statistics `Python` `Defra` `EODS-API` `WPS`
- Select and download S2 granules from EODS, then create mosaic, clip to area of interest and create NDVI. `Python` `JNCC` `EODS-API` `WPS`
- Select and download S2 granules from EODS, then create best-pixel composite using `RSGISLib` `Python` `JNCC` `EODS-API` `WPS` `RSGISLib`

---

## Marine and Coastal Applications 

### Seagrass monitoring
- example

### Satellite-derived bathymetry
- [IMECsentinel](https://github.com/GemmaH131/IMECsentinel)  Bathymetry from Sentinel-2 imagery to detect sandbanks in the southern North Sea. `R` `Newcastle-University`

---

## Terrestrial Applications

### Habitat Change Detection
 - Change detection – workflow for processing input data `R` `JNCC`
 - Change detection Proof of Concept RShiny App `R` `JNCC`
 - Change detection RShiny App 2020 pilot `R` `JNCC`

### Peatland Mapping
- [Bare peat mapping - creating indices](https://github.com/duncansnh/Bare-peat/blob/master/bare_peat_indices.r) - calculates various indices for bare peat mapping vectors too large to apply in one script, therefore carried out with single raster at a time, controlled input by moving rasters between folders on remote sensing drive. `R` `Nature.Scot`
- [Bare peat mapping - creating indices](https://github.com/duncansnh/Bare-peat/blob/master/Indices_creation.ipynb) - Script to create indices from ARD of 10 bands from Sentinel 2. Creates 23 band raster (float 32). `Python` `Nature.Scot`
- [Bare peat mapping – random forest classification](https://github.com/duncansnh/Bare-peat/blob/master/bare.peat.national.RF.classification.R) -  The script reads an ESRI Shapefile (defined by the "shapefile" variable) with training polygons and then selects a user-determined number of samples from each land cover type. A multilayer image that contains spectral, other continuous data or categorical data is also input. For each randomly selected sample the data values for that pixel are determined and these data are used to run the Random Forest model. After building the model the multilayer image is read, and up to three output layers can be selected for the output image. `R` `Nature.Scot`
- [Bare peat mapping – random forest classification](https://github.com/duncansnh/Bare-peat/blob/master/Data_Split_Classification_.ipynb) - Script to perform supervised classification. Applied to bare peat classification on nationwide scale using Sentinel-2. `Python` `Nature.Scot`

### Upland mapping
- example

### Habitat mapping
- [Living England habitat mapping](https://github.com/NE-EEOS/Living-England) - Satellite-based habitat mapping of England. `R` `Natural England`
- [Commons Mapping](https://github.com/NE-EEOS/CommonsMapping) - awaiting description `R` `Natural England`
- [Living Maps](https://github.com/NE-EEOS/LivingMaps) - Automated object-based classification using Random Forest for catchment pioneer `R` `Natural England`

---

## GitHub accounts of relevant organisations
- [Nature.Scot](https://github.com/Scottish-Natural-Heritage) - Scotland's Nature Agency [homepage](https://www.nature.scot/)
- [defra](https://github.com/defra) - UK government department responsible for safeguarding our natural environment, supporting our food & farming industry, and sustaining a thriving rural economy. [homepage](https://www.gov.uk/government/organisations/department-for-environment-food-rural-affairs)
- [CefasRepRes](https://github.com/CefasRepRes) - Cefas is a world leader in marine science and technology, providing innovative solutions for the aquatic environment, biodiversity and food security [homepage](https://www.cefas.co.uk/)
- [cedadev](https://github.com/cedadev) - Centre for Environmental Data Analysis Developers [homepage](http://www.ceda.ac.uk/)

## Other useful Earth Observation GitHub links
- [Awesome-EO-Code](https://github.com/acgeospatial/awesome-earthobservation-code) - A curated list of awesome tools, tutorials, code, helpful projects, links, stuff about Earth Observation and Geospatial stuff! 

<b>End</b>


[Contribution guidelines for this project](CONTRIBUTING.md)

[![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg


###### Work in progress - links are still being added.
