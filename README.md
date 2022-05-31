# Predicting Snow Water Equivalent in regions in Western United States
**Estimating snow water equivalent (SWE) at a high spatiotemporal resolution over the Western U.S. using near real-time data sources**

**Author**: Hanis Zulmuthi

May 2022


![http://url/to/img.png](https://i.pinimg.com/originals/9d/d6/5f/9dd65ffbb09b6bb44e5cbb47df654fd3.jpg)
Source: [Reddit.com](https://www.reddit.com/r/EarthPorn/comments/a6ewla/snow_and_flowing_water_is_one_of_the_most_magical/?utm_source=ifttt)


## Overview
This project budded from a competition titled [Snowcast Showdown](https://www.drivendata.org/competitions/90/competition-reclamation-snow-water-eval/page/431/) on [Driven Data](https://www.drivendata.org/). The goal of the project is to develop a predictive model to estimate the distribution of Snow Water Equivalent (SWE) at a high spatiotemporal resolution over the Western U.S. using near real-time data sources.

## Introduction
Snow Water Equivalent (SWE) is a common snowpack measurement used by hydrologists and water managers to gage amount of liquid water contained within snowpack. It is equal to the amount of water contained within the snowpack when it melts. It can be thought of as the depth of water that would theoretically result if you melted the entire snowpack instantaneously [[1]](#1).  

## Data Understanding
**Ground Measures data:** Ground measures help provide regularly collected, highly accurate point estimates of SWE at designated stations. The ground measures data are from [Snow Telemetry (SNOTEL)](https://www.nrcs.usda.gov/wps/portal/wcc/home/) and [California Data Exchange Center (CDEC)](https://cdec.water.ca.gov/). The dataset used from these sources is available in this repo [here](./data/).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***[SNOTEL](https://www.nrcs.usda.gov/wps/portal/wcc/home/):*** The Snow Telemetry (SNOTEL) program consists of automated and semi-automated data collection sites across the Western U.S.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***[CDEC](https://cdec.water.ca.gov/):*** The California Data Exchange Center (CDEC) facilitates the collection, storage, and exchange of hydrologic and climate information &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; to support real-time flood management and water supply needs in California. CDEC operates data collection sites similar to SNOTEL within &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; California.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ground-based sites from SNOTEL and CDEC are used both as an input data source and in ground truth labels for our predictive model. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;***Note that, sites that we are predicting SWE for, are entirely distinct from those in the features data.***

**[MODIS Satellite Imagery](https://microsoft.github.io/AIforEarthDataSets/data/modis.html):** The satellite imageries from MODIS were not used for modelling due to contraints in computing power and memory. We did however, pull down the satellite images from their [Azure blob]() and saved it as numpy arrays of pixels. This process was done in this [notebook](./src/MODIS-DEM-Preprocessing_colab.ipynb) that was executed in [Google Colab](https://colab.research.google.com/?utm_source=scs-index).


### Notebooks in this repo
[MODIS-DEM-Preprocessing_colab.ipynb](./src/MODIS-DEM-Preprocessing_colab.ipynb) - This notebook c

[Data-Preprocessing.ipynb](./src/Data-Preprocessing.ipynb)

[Modeling.ipynb](./src/Modeling.ipynb)


## Modeling & Results

### Model Comparisons

![r2](./figures/r2.jpeg)

### Best Model

![model performance](./figures/model_performance.jpeg)

## Future Work

**1. Explore Time-Series to forecast SWE at SNOTEL and CDEC stations**

**2. Exploration of feature engineering**
  - Use historical mean for SWE? capture trends 
  - Data from snow day ? capture season

**3. Incorporate data from satellite imageries**


**3. Use near Real-time data to predict SWE**
  - Make a d dashboard of predictions and forecast?

## Repository Structure
  ```
├── data  
├── images
├── src 
│       ├── catboost_info
│       ├── Data-Preprocessing.ipynb
│       ├── MODIS-DEM_Preprocessing_colab.ipynb
│       ├── MODIS-Preprocessing.ipynb
│       ├── Modeling.ipynb
│       └── EDA.ipynb
│
├── .gitignore
├── LICENSE
├── README.md
└── modis.yml 
  ```

## References
<a id="1">[1]</a> 
What is SWE?
(Natural Resources Conservation Service Nevada, [USDA](https://www.nrcs.usda.gov/wps/portal/nrcs/detail/nv/snow/?cid=nrcseprd1746821#:~:text=Snow%20Water%20Equivalent%20(SWE)%20is,the%20snowpack%20when%20it%20melts.))
