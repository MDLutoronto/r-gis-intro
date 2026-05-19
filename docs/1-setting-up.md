---
title: Setting Up
parent: Introduction to GIS using R
layout: default
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer: 
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
    - name: Cole White
      link: https://library.utoronto.ca/staff/cole-white
created_date: 2024-09-19
nav_order: 1
---

## Setting Up

After downloading the datasets used in this tutorial, you want to set the working directory to the folder where you have saved these datasets on your machine using the setwd() function. In the code below, enter the path to your RGISfiles folder. Note that you will need to change all backslashes to forward slashes.

```r
# Set Working Directory
setwd("Enter Path to the RGISfiles Folder")
```
Next, we install and load the necessary packages for this tutorial. The spatial package used is the sf package. We also use the ggplot2, ggspatial and the RColorBrewer packages to make maps.

```r
# Install and Load Packages
install.packages(c("sf", "ggplot2", "ggspatial", "RColorBrewer"))
library(sf)
library(ggplot2)
library(ggspatial)
library(RColorBrewer)
```
**Technique:** [Quantitative Data Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Qualitative+Data+Analysis), [Mapping](https://mdlutoronto.github.io/tutorials-search/?technique=Mapping), [Spatial Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Spatial+Analysis) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Microdata](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Microdata)