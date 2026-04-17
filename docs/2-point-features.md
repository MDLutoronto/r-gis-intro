---
title: Point Features
parent: Introduction to GIS using R
layout: default
nav_order: 2
---

## 1. Point Features

This tutorial will show you how to work with point, line, and polygon features in R. Let’s start with point features. This section will show you how to create a point feature dataset from scratch and then make a map of it.

In this section, we want to create a spatial dataset of four museums from scratch. First, we create three lists of the longitude values, latitude values and museum names for four museums of interest. To create a list in R, you can use the c() function. We keep the order of museums in each list.

Then we combine these three lists using the data.frame() function to create a new dataset. We call this dataset or data frame museums. When we run museums by itself, we can see the three columns longitude, latitude and names for the four museums.

```r
# 1. Point Features
# Creating data using longitude/latitude pairs and names of places
longitude <- c(-79.4094, -79.3946, -79.3322, -79.5169)
latitude <- c(43.6781, 43.6677, 43.7253, 43.7735)
names <- c('Casa Loma', 'Royal Ontario Museum', 'Aga Khan Museum',
           'Black Creek Pioneer Village')
# Convert list to dataframe
museums <- data.frame(longitude, latitude, names)
museums
```
<img src='{{ '/assets/images/1.1%20Museum%20Dataframe.png' | relative_url }}' alt='1.1 Museum Data Frame' title='' width='507' height='121' />

To convert the museums data frame to a spatial dataset or a sf (simple features) object, we use the st_as_sf() function. Inside this function, we specify the museums dataset. Then using the coords argument, we specify the longitude and latitude variable names in our dataset as a list using the c() function. We also specify the coordinate reference system using the crs argument. We save the converted spatial dataset as museums_sf.

Now, when we run museums_sf by itself, we can see that it is a simple feature object with four point features and one field or variable called names.

```r
# Convert dataframe to sf object
museums_sf <- st_as_sf(museums, coords=c("longitude", "latitude"),
                     crs="EPSG:4326") 
museums_sf
```
<img src='{{ '/assets/images/1.2%20Museums%20SF%20Object.png' | relative_url }}' alt='1.2 Museums SF Object' title='' width='625' height='204' />

We can make a map of these museums using ggplot2 functions. To make a basic map, we first initialize the plot area using the ggplot() function. Then we use the geom_sf() function to specify the museums spatial dataset. When we run this, it gives us a map of the latitudes and longitudes of the four museums. 

```r
# Map museums using ggplot2
ggplot() + geom_sf(data=museums_sf)
```
<img src='{{ '/assets/images/1.3%20Museums%20Map.png' | relative_url }}' alt='1.3 Museums Map' title='' width='708' height='516' />