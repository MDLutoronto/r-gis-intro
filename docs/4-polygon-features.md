---
title: Polygon Features
parent: Introduction to GIS using R
layout: default
nav_order: 4
---

## 3. Polygon Features

Let’s move on to polygon features. The spatial dataset we will use for polygon features is the City of Toronto’s neighbourhood boundaries shape file. In the section, we will import and map the Toronto neighbourhood boundaries dataset. We will also import the Toronto cultural hot spots point features dataset to combine it with the neighbourhood dataset later in this tutorial.

The Toronto neighbourhoods dataset is called *Neighbourhoods - 4326.shp*. To import this spatial dataset, we can use the read_sf() function. And we save it as neighbourhoods_sf.

When we run neighbourhoods_sf by itself, we can see that it is a simple features object with 158 polygons or neighbourhoods and 11 fields or variables.

```r
# 3. Polygon Features
# Import Toronto neighbourhoods
neighbourhoods_sf <- read_sf('Neighbourhoods - 4326.shp')
neighbourhoods_sf
```
<img src='{{ '/assets/images/3.1%20Neighbourhoods%20SF%20Object.png' | relative_url }}' alt='3.1 Neighbourhoods SF Object' title='' width='706' height='454' />

To make a basic map of a polygon features spatial dataset using ggplot2, we use the same approach as we did with point features and line features. We initialize the plot area using the ggplot() function then we specify the neighbourhoods sf object using the geom_sf() function.

```r
# Map Toronto neighbourhoods
ggplot() + geom_sf(data=neighbourhoods_sf)
```
<img src='{{ '/assets/images/3.2%20Neighbourhoods%20Map.png' | relative_url }}' alt='3.2 Neighbourhoods Map' title='' width='707' height='515' />

We will also import the Toronto cultural hot spots dataset. This dataset is called *points-of-interest - 4326.shp*. We will combine this dataset with the neighbourhoods dataset in section 5. To import this spatial dataset, we can use the read_sf() function. And we save it as culturalhotspots_sf.

When we run culturalhotspots_sf by itself, we can see that it is a simple features object with 895 point features or hot spots and 29 fields or variables.

```r
# Additional data for Toronto neighbourhoods: Cultural Hot Spots (point features)
culturalhotspots_sf <- read_sf('points-of-interest - 4326.shp')
culturalhotspots_sf
```
<img src='{{ '/assets/images/3.3%20Cultural%20Hot%20Spots%20in%20Toronto%20Neighbourhoods_0.png' | relative_url }}' alt='3.3 Cultural Hot Spots in Toronto Neighbourhoods' title='' width='711' height='427' />
