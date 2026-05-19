---
title: Mapping using ggplot2
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
nav_order: 5
---

## 4. Mapping using ggplot2

In this section, we will cover how to make maps using ggplot2. We will use the neighbourhoods, subway lines, subway stations and museums spatial datasets.

We have covered how to make basic maps in the previous sections. To make a map that includes polygons, lines and point features, you can add each layer individually using the geom_sf() function. We use the order of polygons, lines and point features to have the layer of point features on top of the line features on top of the polygons. 

```r
# 4. Mapping using ggplot2 
# Mapping multiple spatial data layers
ggplot() + 
  geom_sf(data=neighbourhoods_sf) + 
  geom_sf(data=subway_lines_sf) + 
  geom_sf(data=subway_stations_sf) +
  geom_sf(data=museums_sf)
```
<img src='{{ '/assets/images/4.1%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.1 Mapping using ggplot2' title='' width='706' height='514' />

To modify the colour inside the polygon, you can use the colour argument and to modify the colour of the polygon boundaries, you can use the fill argument.

```r
# Polygon features: to modify colours within the polygon and the border
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf) + 
  geom_sf(data=subway_stations_sf) +
  geom_sf(data=museums_sf)
```
<img src='{{ '/assets/images/4.2%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.2 Mapping using ggplot2' title='' width='706' height='514' />

For line features, to modify the colour of the line, we use the colour argument and to modify the line width, we use the linewidth argument.

```r
# Line features: to modify the colour and line width
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf, colour="lightgrey", linewidth=1) + 
  geom_sf(data=subway_stations_sf) +
  geom_sf(data=museums_sf)
```
<img src='{{ '/assets/images/4.3%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.3 Mapping using ggplot2' title='' width='708' height='516' />

For point features, to modify the colour, size and shape of point features, we can use the colour, size and shape arguments respectively. You can find the full selection of possible shapes and their values in the help window by using the R code **help(points)** and going to the pch section.

```r
# Point features: to modify the colour, size, and shape
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf, linewidth=1, colour="lightgrey") + 
  geom_sf(data=subway_stations_sf, colour="lightgrey", size=1.5) +
  geom_sf(data=museums_sf, colour="maroon2", size=3, shape=17)
```
<img src='{{ '/assets/images/4.4%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.4 Mapping using ggplot2' title='' width='705' height='514' />

To apply a theme to the map, we can use one of the ggplot2 theme functions. If you type theme, you should see a dropdown menu with the list of themes that you can use. In this tutorial, we apply the classic theme to this map.

```r
# To apply a theme to the map
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf, linewidth=1, colour="lightgrey") + 
  geom_sf(data=subway_stations_sf, colour="lightgrey", size=1.5) +
  geom_sf(data=museums_sf, colour="maroon2", size=3, shape=17) + 
  theme_classic()
```
<img src='{{ '/assets/images/4.5%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.5 Mapping using ggplot2' title='' width='708' height='516' />

To add a title, we use the ggtitle() function. We also add a subtitle using the subtitle argument.

```r
# To add a title
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf, linewidth=1, colour="lightgrey") + 
  geom_sf(data=subway_stations_sf, colour="lightgrey", size=1.5) +
  geom_sf(data=museums_sf, colour="maroon2", size=3, shape=17) + 
  theme_classic() +
  ggtitle("Museums and Subway Lines",
          subtitle="Toronto, Canada")
```
<img src='{{ '/assets/images/4.6%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.6 Mapping using ggplot2' title='' width='708' height='516' />

To add a scale, we use the annotation_scale() function from the ggspatial package. To place the scale in the bottom right corner of the map, we assign the location argument the value “br”. Then we use the bar_cols argument to select the two alternating colours of the scale. We use the R colours grey20 (a dark grey) and white. 

```r
# To add a scale bar (package: ggspatial)
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf, linewidth=1, colour="lightgrey") + 
  geom_sf(data=subway_stations_sf, colour="lightgrey", size=1.5) +
  geom_sf(data=museums_sf, colour="maroon2", size=3, shape=17) + 
  theme_classic() +
  ggtitle("Museums and Subway Lines",
          subtitle="Toronto, Canada") +
  annotation_scale(location = "br", bar_cols = c("grey20", "white"))
```
<img src='{{ '/assets/images/4.7%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.7 Mapping using ggplot2' title='' width='707' height='515' />

To add a north arrow, we use the annotation_north_arrow() function from the ggspatial package. Using the location argument, we place the north arrow in the bottom right corner of the map. To point the arrow to the true north, we set the argument which_north to “true”.

The pad_x and the pad_y arguments are used to specify the distance of the arrow from the edge of the frame. We specify the distances from the edge in units of inches here but you can also use centimetres for example.

Finally, the style argument is used to specify the drawing style of the arrow. You will find the full selection of north arrow drawings [here](https://cran.r-project.org/web/packages/ggspatial/ggspatial.pdf#Rfn.north.Rul.arrow.Rul.orienteering). We are using the north_arrow_nautical() style here. For this specific style, we select the two alternating colours used to fill the arrow using the fill argument and the colour of the border of the arrow using the line_col argument.

```r
# To add the north arrow (package: ggspatial)
ggplot() + 
  geom_sf(data=neighbourhoods_sf, colour="darkgrey", fill="#354f52") +
  geom_sf(data=subway_lines_sf, linewidth=1, colour="lightgrey") + 
  geom_sf(data=subway_stations_sf, colour="lightgrey", size=1.5) +
  geom_sf(data=museums_sf, colour="maroon2", size=3, shape=17) + 
  theme_classic() +
  ggtitle("Museums and Subway Lines",
          subtitle="Toronto, Canada") +
  annotation_scale(location = "br", bar_cols = c("grey20", "white")) +
  annotation_north_arrow(location = "br", which_north = "true",
                         pad_x = unit(0.1, "in"), pad_y = unit(0.3, "in"),
                         style = north_arrow_nautical(fill = c("grey40", "white"),
 line_col = "grey20"))
```
<img src='{{ '/assets/images/4.8%20Mapping%20using%20ggplot2.png' | relative_url }}' alt='4.8 Mapping using ggplot2' title='' width='708' height='516' />

**Technique:** [Quantitative Data Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Qualitative+Data+Analysis), [Mapping](https://mdlutoronto.github.io/tutorials-search/?technique=Mapping), [Spatial Analysis](https://mdlutoronto.github.io/tutorials-search/?technique=Spatial+Analysis) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Microdata](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Microdata)