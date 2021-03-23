# Sentinel-1 & Sentinel-2 ARD code list



![logos](images/Logos_updated.png)  


A curated list supporting the use of Sentinel-1 and Sentinel-2 analysis-ready data (ARD) in the UK

---

# Project Background
[JNCC](https://jncc.gov.uk/) are leading a project to help people use [Sentinel-1](https://sentinel.esa.int/web/sentinel/missions/sentinel-1) and [Sentinel-2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2) analysis-ready data ([ARD](https://jncc.gov.uk/our-work/simple-ard-service-faqs/)) provided by the [Defra EO Data Service](https://defradigital.blog.gov.uk/2020/06/18/making-it-easier-to-access-and-use-earth-observation-data/) and the [CEDA Archive](http://archive.ceda.ac.uk/), with a particular focus on accessing data via API (application programming interfaces).  As part of this project, we have set up a public repository for sharing code in any language for processing or analysing Sentinel-1 and Sentinel-2 ARD.  We conducted a survey in July 2020 to gain a better understanding of user needs and inform the choice of code-sharing platform.  Based on the survey results and subsequent discussion with the project team and partners, it was agreed that the best option was to set up this curated list on GitHub.  We have also set up a Slack workspace to enable discussion and messaging between users of Sentinel-1 and Sentinel-2 ARD; you can [join the group here](https://S1-S2-ARD-users.slack.com/) if you have a Slack account, or [sign up here](https://join.slack.com/t/s1-s2-ard-users/signup) if you do not yet have a Slack account. 

# How to contribute
This list is a work in progress and we need your help to keep it up-to-date!  If you have examples of code for selecting, downloading, manipulating or analysing Sentinel-1 or Sentinel-2 ARD, please add them to the list by making a pull request.  See our [contribution guidelines](CONTRIBUTING.md) for details on how to do this. 

# Acknowledgements
Thank you very much to all the [authors](S1_S2_ARD_authors.txt) who have contributed their code to this list, and to [Andrew Cutts](https://github.com/acgeospatial) for help with setting up the list.
This project is funded by the Caroline Herschel Framework Partnership Agreement on [Copernicus User Uptake](https://jncc.gov.uk/our-work/copernicus-project/). 

---

# Contents

|   [<b>Tutorials and functions</b>](#tutorials-and-functions )   |    [Defra EO Data Service API](#defra-eo-data-service-api)    |    [CEDA API](ceda-api)    |    [Other functions](other-functions) <br>

|   [<b>Marine and Coastal Applications</b>](#marine-and-coastal-applications)   |   [Maerl monitoring](#maerl-monitoring)   |   [Satellite-derived bathymetry](#satellite-derived-bathymetry)   |   [Intertidal extent mapping](#mapping-intertidal-extent) <br>

|   [<b>Terrestrial Applications</b>](#terrestrial-applications)   |   [Habitat Change Detection](#habitat-change-detection)   |   [Peatland Mapping](#peatland-mapping)   |   [Burn mapping](#burn-mapping)   |  [Habitat mapping](#habitat-mapping)   |
   
|   [GitHub accounts of relevant organisations](#GitHub-accounts-of-relevant-organisations)   |   [Other useful Earth Observation GitHub links](#other-useful-earth-observation-github-links)   |           

<b>Start Here</b>

## Tutorials and functions 
### Defra EO Data Service API
#### EODS API training materials
*These Jupyter Notebooks were created as training materials to demonstrate use of the EO Data Service API. They were produced before the [EODS API Python Library](#eods-api-python-library) was developed. Many of the processes in these Notebooks can now be carried out more efficiently using the functions in the EODS API Python Library.*
- ['eods-api-example-simple-query'](https://github.com/defra-data/EODS-API/blob/master/eods-api-example-simple-query.ipynb). Introduction to the Defra EO Data Service API and creating a simple query. `Python` `Defra` `EODS-API`
- ['eods-api-example-generate-cloudless-mosaic'](https://github.com/defra-data/EODS-API/blob/master/eods-api-example-generate-cloudless-mosaic.ipynb). Generate a list of Sentinel-2 granules with least cloud per granule per orbit for a given date range and geographic area. `Python` `Defra` `EODS-API`
- ['eods-api-example-wps'](https://github.com/defra-data/EODS-API/blob/master/eods-api-example-wps.ipynb).  Use web processing services (WPS) to clip raster, select single band from raster, re-project raster, create points from raster, and generate zonal statistics `Python` `Defra` `EODS-API` `WPS`
- ['EODS_API'](https://github.com/jncc/defra-eo-data-service-api/blob/master/EODS_API.ipynb) Download Sentinel-2 data via API from the Defra EO Data Service, then create a mosaic, clip to area of interest and create NDVI. `Python` `JNCC` `EODS-API` `WPS` `copernicus-user-uptake`
- ['EODS_API_Best_pixel'](https://github.com/jncc/defra-eo-data-service-api/blob/master/EODS_API_Best_pixel.ipynb).  Download Sentinel-2 data via API from the Defra EO Data Service, then create best-pixel composite using the pixels with least cloud in a stack of imagery from different dates `RSGISLib` `Python` `JNCC` `EODS-API` `WPS` `copernicus-user-uptake`
- [config.py](https://github.com/defra-data/EODS-API/blob/master/config.py). Config file for use with the above Jupyter Notebooks, e.g. to input your authentication token.
- [environment.yml](https://github.com/defra-data/EODS-API/blob/master/environment.yml).  Environment file for use with the Jupyter Notebooks in this section and the section below.
#### EODS API Python library 
*A module of library functions for programmatic interaction with the EO Data Service developed by Sam Franklin at CGI, together with four Jupyter Notebooks demonstrating applications of the library for filtering, downloading and manipulating Sentinel-2 data.*
- [eodslib.py](https://github.com/defra-data/EODS-API/blob/master/eodslib.py). Functions for interacting with the EO Data Service.  Examples include: keyword arguments for filtering data; finding the least cloudy Sentinel-2 granules; creating XML files for use in Web Processing Service (WPS) requests; submitting WPS requests; removing split Sentinel-2 granules from a dataframe; processing data downloaded via WPS (unzipping and renaming files, deleting zip files). `Python` `Defra` `EODS-API` `WPS`
- [eodslib.py example 1: simple query](https://github.com/defra-data/EODS-API/blob/master/eods%20example1%20-%20simple%20EODS%20query.ipynb).  Apply filter parameters and return results as a dataframe. `Python` `Defra` `EODS-API` 
- [eodslib.py example 2: query and download](https://github.com/defra-data/EODS-API/blob/master/eods%20example2%20-%20query%20EODS%20and%20download%20results.ipynb).  Apply filter parameters and download returned data. `Python` `Defra` `EODS-API` `WPS`
- [eodslib.py example 3: query, download, optimise and mosaic](https://github.com/defra-data/EODS-API/blob/master/eods%20example3%20-%20query%20EODS%20-%20download%20results%20-%20optimise%20s2s%20-%20mosaic%20s2s.ipynb).  Apply filter parameters, download results, convert downloaded files to 'optimised' GEOTIFFs and mosaic the imagery by creating a virtual raster. `Python` `Defra` `EODS-API` `WPS`
- [eodslib.py example 4: query, download clipped area, calculate ndvi](https://github.com/defra-data/EODS-API/blob/master/eods%20example4%20-%20query%20eods%20-%20coveragecrop%20download%20-%20calc%20ndvi%20-%20plot%20ndvi.ipynb).  Apply filter parameters, download the returned data clipped to an area of interest, calculate and plot NDVI from the downloaded data. `Python` `Defra` `EODS-API` `WPS`
### CEDA API
- examples coming soon
### Other functions 
- ['habitat-condition-monitoring'](https://github.com/jncc/habitat-condition-monitoring).  A package of various functions involved in preparation, statistical analysis and modelling with Sentinel-1 and Sentinel-2 data, including cloud and shadow masking, calculating indices, creating thumbnails, generating zonal statistics and summarising these per polygon. `R` `JNCC` `copernicus-user-uptake`
- [Generate coherence image from Sentinel-1](https://github.com/jncc/cuu-illegal-waste).  Please note this uses Sentinel-1 *Single Look Complex (SLC)* data, not the analysis-ready data processed by JNCC and Defra. XML script and supporting command line scripts to produce a coherence image from two SLC input datasets, enabling detection of ground surface changes over time. `JNCC` `SEPA` `copernicus-user-uptake`

---

## Marine and Coastal Applications 

### Maerl monitoring
- example coming soon

### Satellite-derived bathymetry
- [IMECsentinel](https://github.com/GemmaH131/IMECsentinel)  Bathymetry from Sentinel-2 imagery to detect sandbanks in the southern North Sea. `R` `Newcastle-University`

### Mapping intertidal extent
- example coming soon

---

## Terrestrial Applications

### Habitat Change Detection
 - Workflow for processing Sentinel-1 and Sentinel-2 with habitat map shapefiles to produce input data for change detection RShiny app, using functions provided in the ['habitat-condition-monitoring'](https://github.com/jncc/habitat-condition-monitoring) package.  There are separate workflows for [English sites](https://github.com/jncc/cuu-change-detection/blob/master/CUUCD_EnglishSites.Rmd), [Welsh sites](https://github.com/jncc/cuu-change-detection/blob/master/CUUCD_WelshSites.Rmd) and [Scottish sites](https://github.com/jncc/cuu-change-detection/blob/master/CUUCD_ScottishSites.Rmd). `R` `JNCC` `copernicus-user-uptake`
 - ['change-analysis-examples'](https://github.com/jncc/cuu-change-detection/blob/master/change_analysis_examples.Rmd) A short analysis of NDVI statistics generated from Sentinel-2 and how they can be used in conjunction with a habitat map shapefile to identify polygons which deviate from mean values by more than set thresholds. `R` `JNCC` `copernicus-user-uptake`
 - ['change-statistics-analysis'](https://github.com/jncc/cuu-change-detection/blob/master/change_statistics_analysis.Rmd). An interactive document demonstrating use of NDVI derived from Sentinel-2 in conjunction with a habitat map shapefile to identify polygons which deviate from mean values by more than set thresholds. `R` `JNCC` `copernicus-user-uptake`
 - Change detection RShiny App 2020 pilot - coming soon `R` `JNCC` `copernicus-user-uptake`

### Peatland Mapping
#### Nature.Scot bare peat mapping
- [Bare peat mapping - creating indices](https://github.com/duncansnh/Bare-peat/blob/master/bare_peat_indices.r).  Calculates various indices for bare peat mapping vectors too large to apply in one script, therefore carried out with single raster at a time, controlled input by moving rasters between folders on remote sensing drive. `R` `Nature.Scot`
- [Bare peat mapping - creating indices](https://github.com/duncansnh/Bare-peat/blob/master/Indices_creation.ipynb).  Creates indices from ARD of 10 bands from Sentinel-2. Creates 23 band raster (float 32). `Python` `Nature.Scot`
- [Bare peat mapping – random forest classification](https://github.com/duncansnh/Bare-peat/blob/master/bare.peat.national.RF.classification.R).  The script reads an ESRI Shapefile (defined by the "shapefile" variable) with training polygons and then selects a user-determined number of samples from each land cover type. A multilayer image that contains spectral, other continuous data or categorical data is also input. For each randomly selected sample the data values for that pixel are determined and these data are used to run the Random Forest model. After building the model the multilayer image is read, and up to three output layers can be selected for the output image. `R` `Nature.Scot`
- [Bare peat mapping – random forest classification](https://github.com/duncansnh/Bare-peat/blob/master/Data_Split_Classification_.ipynb).  Script to perform supervised classification. Applied to bare peat classification on nationwide scale using Sentinel-2. `Python` `Nature.Scot`
#### JNCC Bare Peat Mapper app 
- [Bare peat mapping functions](https://github.com/jncc/bare-peat-mapping-pilot).  A set of R functions developed for a [JNCC pilot study](https://hub.jncc.gov.uk/assets/958df51f-2e7c-4d2b-92f0-eac84c2a86af) on using EO to monitor peatland condition.  Functions include detecting bare peat in Sentinel-2 imagery using Random Forest classification and regression modelling. `R` `JNCC` `copernicus-user-uptake`
- ['CUUPeatApp_map_prep'](https://github.com/jncc/cuu-peatland-mapping/blob/master/scripts/CUUPeatApp_map_prep.R).  Prepares Sentinel-2 and bare peat layers for use in the Bare Peat Mapper app, using functions provided in the ['habitat-condition-monitoring'](https://github.com/jncc/habitat-condition-monitoring) package. `R` `JNCC` `copernicus-user-uptake`
- Markdown documentation detailing the process of using Sentinel-2 imagery and a spatial framework of polygons to study change in bare peat at the following sites: 
    - Caithness and East Sutherland, Scotland [fine-scale mapping](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/FR_CES_Fine.Rmd) and [time-series modelling](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/FR_CES_Broad.Rmd)
    - Dark Peak, England [fine-scale mapping](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/NE_DarkPeak_Fine.Rmd) and [time-series modelling](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/NE_DarkPeak_Broad.Rmd) 
    - Humberhead NNR, England [fine-scale mapping](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/NE_Humberhead_Fine.Rmd) and [time-series modelling](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/NE_Humberhead_Broad.Rmd)
    - Brecon Beacons, Wales [fine-scale mapping](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/WG_Brecon_Fine.Rmd) and [time-series modelling](https://github.com/jncc/cuu-peatland-mapping/blob/master/site%20docs/WG_Brecon_Broad.Rmd).

### Burn mapping
Code developed by Nature.Scot as part of the Copernicus User Uptake project on upland burn mapping from Sentinel 2.
The code has been developed in Python in Jupyter notebooks designed to work in a Google Colabs environment, though it should only need minor changes to work in other environments.  Project still in progress so code may change.
- [Burn extent indices](https://github.com/duncansnh/burn-mapping/blob/master/CUU_burn_extent_indices.ipynb) - Script to create indices from ARD of 10 bands from Sentinel 2. Creates rasters float 32. `copernicus-user-uptake` `Python` `Nature.Scot`
- [Burn extent box plots of pixel values](https://github.com/duncansnh/burn-mapping/blob/master/CUU_burn_extent_pixel_box_plots.ipynb) - Script to extract pixel values from a raster relating to a set of training polygons and then generate box plots using seaborn python package. `copernicus-user-uptake` `Python` `Nature.Scot`
- [Burn extent image thresholding](https://github.com/duncansnh/burn-mapping/blob/master/CUU_burn_extent_image_thresholding.ipynb) - Script to threshold an input image based on one or more spectral index thresholds `copernicus-user-uptake` `Python` `Nature.Scot`

Code developed by Pixalytics and EnviroSAR for the Defra EO Centre of Excellence R&D project: 'Upland Burn Detection with Radar'
A [set of Jupyter notebooks and example data](https://github.com/pixalytics-ltd/upland-burn-detection) to: 
- download Sentinel-1 ARD for a user-defined area and timeframe `Python` `Defra`
- process Sentinel-1 coherence data for a user-defined area and timeframe `Python` `Defra`
- analyse the ARD and coherence data and generate an interactive map of burns `Python` `Defra`
- automate detection of burns from Sentinel-1 data based on threshold values `Python` `Defra`

### Habitat mapping
- [Living England habitat mapping](https://github.com/NE-EEOS/Living-England) - Satellite-based habitat mapping of England. `R` `Natural England`
- [Commons Mapping](https://github.com/NE-EEOS/CommonsMapping) - Commons mapping in England `R` `Natural England`
- [Living Maps](https://github.com/NE-EEOS/LivingMaps) - Automated object-based classification using Random Forest for catchment pioneer `R` `Natural England`

---

## GitHub accounts of relevant organisations
- [Nature.Scot](https://github.com/Scottish-Natural-Heritage) - Scotland's Nature Agency [homepage](https://www.nature.scot/)
- [defra](https://github.com/defra) - UK government department responsible for safeguarding our natural environment, supporting our food & farming industry, and sustaining a thriving rural economy. [homepage](https://www.gov.uk/government/organisations/department-for-environment-food-rural-affairs)
- [CefasRepRes](https://github.com/CefasRepRes) - Cefas is a world leader in marine science and technology, providing innovative solutions for the aquatic environment, biodiversity and food security [homepage](https://www.cefas.co.uk/)
- [cedadev](https://github.com/cedadev) - Centre for Environmental Data Analysis Developers [homepage](http://www.ceda.ac.uk/)

## Other useful Earth Observation GitHub links
- [Awesome-EO-Code](https://github.com/acgeospatial/awesome-earthobservation-code) - A curated list of awesome tools, tutorials, code, helpful projects, links, stuff about Earth Observation and Geospatial stuff! 
- [Awesome-SAR](https://github.com/RadarCODE/awesome-sar) - A curated list of awesome synthetic aperture radar (SAR) software, libraries and resources.

<b>End</b>


[Contribution guidelines for this project](CONTRIBUTING.md)



This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

![CC_BY][cc-by-shield]

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg



