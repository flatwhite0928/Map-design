# Map-design

## Data preprocessing

1. Download the crashes geojson data. Generate a hexagonal grid over DC with ```turf.hexGrid```.

2. Aggregate crashes data points according to which hexagonal grid the point resides inside, using ```turf.booleanPointInPolygon```.

3. Find the center point of each hexagon with ```turf.centroid```. Take the center point as the coordinate of features in the heatmap, the cumulative crashes in each hex as one of its properties.

## Map
The center of map was set to Mapbox DC, starting with a zoom level 10.7.

### The heatmap Layer
The heatmap layer is built based on the cumulative crashes we obtained in the data preprocessing. 
![](/img/heatmap.png)

### The Circle and Text Layers
When you keep zooming in, the heatmap gradually disappeared and instead the circle and text layers take the place to offer more detailed information, i.e. number of crashes occured.
![](/img/circle.png)

### The Fill Layer
Finally, when you zoom to 13, the outlines of polygons are added. You can now identify which hexagon does a specific address belongs to. Hexasgons are colored according to the number of crashes occured.
![](/img/fill.png)

### Geocoder
Added a geocoder control to help users search for places.
![](/img/geocoder.png)

## Deliver Map
```heatmap_style.html``` created the map using the style and layers customed on Mapbox Studio.

```heatmap_script.html``` created the map using mapbox-gl-js API. It has the data source from aggregated crashes geojson, four layers and a geocoder control, delivering a similar map with the one using Mapbox Studio.