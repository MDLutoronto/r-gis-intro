---
title: Line Features
parent: Introduction to GIS using R
layout: default
nav_order: 3
---

## 2. Line Features

Let’s move on to line features. The spatial dataset we will use is the City of Toronto’s TTC subway lines dataset. In the section, we will import and map subway lines. We will also map the subway lines with subway stations to show you how to map line and point features together.

The TTC subway lines dataset is called *TTC_SUBWAY_LINES_WGS84.shp*. To import this spatial dataset, we can use the read_sf() function. And we store it as a dataset called subway_lines_sf.

When we run subway_lines_sf by itself, we can see that it is a simple features object with four lines and three fields or variables.

```r
# 2. Line Features
# Import data
subway_lines_sf <- read_sf('TTC_SUBWAY_LINES_WGS84.shp')
subway_lines_sf
```
<img src='{{ '/assets/images/2.1%20Subway%20Lines%20SF%20Object.png' | relative_url }}' alt='2.1 Subway Lines SF Object' title='' width='710' height='268' />

To make a basic map of a line features spatial dataset using ggplot2, we use the same approach as we did with point features. We initialize the plot area using the ggplot() function then we specify the subway lines sf object using the geom_sf() function.

```r
# Map subway lines
ggplot() + geom_sf(data=subway_lines_sf)
```
<img src='{{ '/assets/images/2.2%20Subway%20Lines%20Map.png' | relative_url }}' alt='2.2 Subway Lines Map' title='' width='709' height='517' />

Next, we will import the subway stations CSV file to add subway stations to the map above. To import this subway stations dataset, we use the read.csv() function and we store it as subway_stations.

To convert it to a spatial dataset or an sf object, we use the st_as_sf() function. We specify the longitude and latitude variables using the coords argument and we specify the coordinate reference system using the crs argument. Then we store this sf object as subway_stations_sf. Now we can add it to the subway lines map above.

```r
# Additional data for subway lines: subway stations
# Import CSV file & convert dataframe to sf object
subway_stations <- read.csv('subway_stations.csv')
subway_stations_sf <- st_as_sf(subway_stations, coords=c('lon', 'lat'), crs=4326)
```
To make a basic map of the subway lines with the subway stations, we initialize the plot area using ggplot(). Then using the geom_sf() function, we specify the subway lines first then the subway stations afterwards. This order places the layer of point features or subway stations above the layer of subway lines on the map.

```r
# Map subway lines with subway stations
ggplot() + geom_sf(data=subway_lines_sf) +
  geom_sf(data=subway_stations_sf)
```
<img src='{{ '/assets/images/2.3%20Subway%20Lines%20and%20Subway%20Stations%20Map.png' | relative_url }}' alt='2.3 Subway Lines and Subway Stations Map' title='' width='708' height='516' />