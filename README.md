# Atmospheric Responses to North American Boreal Wildfires

Welcome to the GitHub repository for our thesis project (module 12-GEO-M-RS01) on investigating atmospheric responses to the 2014-2015 North American boreal wildfires utilizing a space-for-time approach.

## Table of Contents
Optional

## Introduction

This thesis project explores the impact of the 2014-2015 North American boreal wildfires on atmospheric dynamics due to the vegetation loss in post-fire ecosystems.
Here, we utilize a space-for-time approach to investigate remotely-sensed wildfire effects on temperature and precipitation. The space-for-time method, as described by [Liu et al. 2019](https://www.nature.com/articles/s41467-018-08237-z), allows for the comparison of data from fire pixels with data from adjacent unaffected control pixels, effectively substituting time with space. The key challenge lies in identifying a matching control pixel for each fire pixel, exhibiting comparable ecological characteristics regarding vegetation type, kNDVI, or GPP. This way, confounding factors such as background climate or vegetation type are being removed.

In this repository, you will find the code, data, and documentation used in our research. We provide methodology and instructions for reproducing our results and conducting further analysis. 


## Method Overview

We developed a four-step procedure for carrying out the space-for-time analysis in post-fire ecosystems.

1. Identification of Fire and Control Pixels:
Fire pixels are identified based on the sum of burned areas for 2014 and 2015.
Unburned pixels are selected as candidate control pixels if they share the same ESA land cover class as the fire pixel.

2. Refinement of Control Pixel Selection:
Additional criteria, including ecological behavior indicators such as ∆kNDVI, ∆T, ∆Rn, and ∆GPP, are used to ensure similarity between fire and control pixels.
Control pixels are selected based on thresholds determined by Liu et al. (2019) and expert knowledge.

3. Assignment of Control Pixels:
The closest control pixel to each fire pixel is identified using Euclidean distance.

4. Analysis:
Monthly mean differences in temperature and precipitation between fire and control pixels are calculated for up to two years after the fire event.

## Installation
To run the analysis code for the thesis, ensure you have Miniconda installed as your package manager. Then, install the necessary Python packages using the following commands:

```bash
conda install -c conda-forge xarray gdal numpy pandas netcdf4 matplotlib scipy;

## Data

All data, besides land cover data, was downloaded from the Earth System Data Lab (ESDL). This data hub provides analysis-ready Earth system data from multiple sources in the form of data cubes. For more information on data cubes, please see [Mahecha et al. 2020](https://esd.copernicus.org/articles/11/201/2020/). 
Data for every variable can be downloaded from the [ESDL webpage](https://deepesdl.readthedocs.io/en/latest/datasets/ESDC/) (last checked: 10 March 2024), along with a detailed description of the dataset as well as information about the initial data and processing. All data has been resampled by ESDL to a temporal resolution of 8 days and a spatial resolition of 0.25°. The data files are provided in the .zarr format.

For land cover data, we used the ESA CCI dataset. This dataset comprises remotely-semsed land cover classification maps. Global annual land cover maps from 1992-2015 can be downloaded [here](https://catalogue.ceda.ac.uk/uuid/b382ebe6679d44b8b0e68ea4ef4b701c?jump=related-docs-anchor) as netCDF and GeoTiff files. For our analysis, we used version 2.0.7. The initial dataset has a spatial resolution of 300 m. To adjust it to the ESDL datasets, resampled it to 0.25° using the the mode-function from the Raster Alignment Tool in QGIS version 3.32.3. 
