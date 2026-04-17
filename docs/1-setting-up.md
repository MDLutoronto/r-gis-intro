---
title: Setting Up
parent: Introduction to GIS using R
layout: default
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
