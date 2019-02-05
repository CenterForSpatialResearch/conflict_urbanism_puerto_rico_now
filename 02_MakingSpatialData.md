## Tutorial 7: Georeferencing

In this exercise, you will explore some of the georeferencing tools available in QGIS and use them to georeference a 1940 map of San Juan. You will learn how to use GIS tools to georectify raster datasets. You will then use the georeferenced map to digitize vector features from the map.


## Part I - Georeferencing a scanned paper map

### Notes on the data

The map you will be using for this exercise is a map published by the U.S. Geological Survey in 1940. This map is in the public domain and thus we can use it freely. The version we are using was made available by the Library at the University of Texas at Austin. The original is available for download [here](http://legacy.lib.utexas.edu/maps/topo/puerto_rico/).

You are going to use [OpenStreetMap](https://www.openstreetmap.org/about) (OSM)  as reference data for the georeferencing process.  OSM provides a free, open-source map of the world from public domain and volunteered data. Please note: OSM map tiles use the Web Mercator projection, for the purposes of this tutorial this is a fine projection to use. However if you are working on creating geospatial data from historic sources you should find and use a projection system that is specifically designed for the local geography you are working in.

### Before you begin
If you haven't already, download the GitHub repository for this course. Using the green button [here](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials), select `Download ZIP`. The Data folder will then have all of the datasets needed for tutorials.

### Setting up QGIS

`Open` QGIS.

You are going to use Open Street Map data as the reference data for the georeferencing process. You can view the OSM basemap service is QGIS through the OpenLayers plugin. This plugin does not come pre-installed with QGIS, so you will probably need to add it. Under the plugins menu, select “Manage and Install Plugins…”
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef2_.png)

The plugins dialog will open.  Search for “Openlayers Plugin.”  Highlight it, and click “Install plugin”:

![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef3_.png)

It may take a few seconds to install.  Close the plugins menu when finished.  The OpenLayers tools should now appear under the Web menu:

![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef4_.png)

This plugin will allow you to view a number of basemap services and steam them directly into your QGIS workspace.  Choose the OpenStreetMap>OpenStreetMap option.
Since you are working in a new QGIS project, the map should show the entire earth as the default:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef5_.png)
Use the zoom in tool ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef6_.png) and zoom into San Juan, Puerto Rico.

![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef07.png)
Now you will access the georeferencing tools and match the scanned map to the OSM map.  

Under the Raster menu, select Georeferencer>Georeferencer:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/geoRef08.png)

(If the Georeferencer menu is missing, you may need to activate the plugin. Go to Plugins>Manage and install plugins and click on the "Installed" tab. Make sure Georeferencer GDAL is checked.)

The Georeferencer screen will open:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef9_.png)

Click on the Add Raster button ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef10a_.png) and navigate to the JPEG image "topo-pr-san_juan-1940.jpg" within the `Data/Raster` folder you downloaded with the repository to this course.  

It will appear in the georeferencer window:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef10.png)

Many aspects of San Juan have clearly changed since this map was drawn, including coastlines, filling in wetlands, new and expanded roads. However we can still identify places that have remained largely the same.
We will find and use these places to georeference the map: matching physical features represented on the map with their current counterparts (and their known coordinates). Because many of the features in this map have changed or no longer exist you will need to be very careful to choose locations that you are confident match up well with their contemporary counterparts. Fortunately, some things have not changed.

### Adding a Point
The QGIS georeferencer does not allow you to view both the scanned map and the workspace at the same time, so you will have to inspect both maps in turn and choose carefully to select locations to add georeferencing control points.
One candidate is the fortified areas near Punta Del Morro in the north west corner of the map.  Use the georeferencer zoom tools ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef11_.png) to zoom to this area. ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef11.png)

Identify as precise a location as possible (a corner of the dock will work nicely) and click on it in the georeferencing window using the add point tool ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef17_.png) When you do so, the Enter map coordinates window appears:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef14_.png)

If we knew the coordinates of this location, we could now add them manually, but since we do not, we must select them from the OSM data in the main QGIS window.  Click on the ![blank](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/GeoRef15_.png) button to see the QGIS workspace.  
You may want to use the QGIS zoom tools to zoom in very close to the point.
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef12.png)

(You may need to reactivate the add button tool ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef17_.png) by maximizing the georeferencing window and clicking the ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef18_.png) button again).  

Once you select the same location on the main workspace window (the OSM window), you will automatically be brought back to the georeferencing window where the assigned coordinates will be imputed (you will have different numbers).  
![blank](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/GeoRef19_.png)

At this point, if you are dissatisfied, you can move the assigned control points with the move GCP point tool ![blank](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/GeoRef20_.png) or delete it entirely and start over with the delete point tool ![blank](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/GeoRef21_.png)
If satisfied, click the OK button and the point will be assigned and appear on the map.  Also, a link table entry will be generated on the bottom of the window:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef13.png)

### More points

To add a second point, repeat the same process. It is a good idea to choose control points that are evenly spaced and well distributed across the map.

Looking for curved streets or other odd landmarks is a good strategy. Get familiar with your historic map and then compare notable locations with the present day map you are georeferencing against.

You will need to add a minimum of five control points to complete the georeferencing (although more is generally better).

Be careful to make sure that the control points you add do in fact match. This can be quite tricky as many of the features have changed.  

I have selected five control points in this example:

![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef16.png)

It is good practice to save the table of control points that you are building. To do this, choose `File>Save GCP points as` and save it in the .points format in the same location as the image. This will allow you to later recreate the work you have done:

Next, you will “transform” the image and create a georeferenced version of the scanned map image. In the georeferencer window, `click` on the transformation settings icon (the yellow gear icon).

Here you can select the transformation type (Polynomial 1 should be appropriate here), resampling method (Cubic is often used for resampled images and photos), output location and name, and the spatial reference system (here I have selected EPSG:3857, the pseudo Mercator projection used in the OSM data). You can also opt to have the georeferenced layer added to QGIS when finished:

![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef19.png)

Close the settings options and click on the start georeferencing button ![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/GeoRef29_.png). This will usually take some time (up to a few minutes depending on your computer).

After the transformation finishes, you should see the map appear in the QGIS workspace.

You can make the scanned map layer partially transparent in the layer properties.  Right click on the map in the layer panel and select properties. On the left panel in the properties dialog, select Transparency, here you can adjust the global transparency with a slider:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef22.png)

Compare the georeferenced map with the Open Street Map layer.  Make sure that features appear to match up closely:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef23.png)

In the next section, you will be using the map you georeferenced here and digitizing some of the features from it.

Export your georeferenced layer as a GeoTiff - be sure to select 'Rendered Image' and CRS 4326 (Psuedo Mercator). Rendered image will remove the black background. CRS 4326 because that is what all webmaps use.


## Part II - Making Vector Data from Raster Data

In this next section we will use the historic map of San Juan that we have just georeferenced in order to digitize (aka trace) certain historic features of the city. This is a key way in which new vector data (shapefiles) are created from historic or non-digital sources. There are lots of potential applications of these methods, from participatory mapping with community groups to historical research and more.

We in the next part of this exercise we will digitize features from the 1940 USGS map of San Juan. Specifically we will learn how to create a new point layer and will then digitize the named buildings from the map as points, and then we will create a new polyline layer and will digitize sections of coastline.

Toggle visibility of the OSM layer off. Remove any transparency from the georeferenced map layer.
Zoom in to the northern coast of San Juan.

First we will create a new point layer. To do this, select `Layer>Create Layer> New Shapefile Layer`. ![create layer](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georeference-newShape.png)

In the new vector dialog layer, choose type “Point”.  Make sure that the CRS is set to `EPSG: 3857 WGS 84 / Pseudo Mercator`. In general the projection of a new layer you are digitizing from a georefereneced source material should match the projection of that georeferenced map. You can also create additional attribute fields for your dataset, if applicable.  Here, I have added a building "name" attribute and made it a text field with a maximum length of 200.  Select OK:

![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef28.png)

Save the new file in the same directory with your map, and name it `NamedBuildings_SanJuan`.

 The layer will now appear in the Layers panel.

To begin creating new features `Click` the toggle editing tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/Digitize9.png) while the buildings layer is highlighted in the layers panel.  Now you can use the add feature tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/Digitize10.png) to start creating buildings.  Click on one of the buildings in the map.  An attribute dialog appears where you can type in attribute information for the feature you just created:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef30.png)

I have entered the name of the building as it is labeled on the map as well as a numeric ID for the building. `Click` OK when finished.

Continue to digitize buildings in this corner of Bombay:
![blank](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/tree/master/Images/georef31.png)

If you want to move one of the point features you can use the move feature tool ![DigitizingExercise](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/Digitize13.png) if you want to delete a feature, you can select it with the select features tool ![DigitizingExercise](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/Digitize14.png) at use the delete key on the keyboard.  It is a good idea to regularly use the “save for selected laters” function to save your work as you digitize:  
![DigitizingExercise](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/Digitize15.png)

When finished, click the toggle editing tool ![DigitizingExercise](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/Digitize16.png) to close the editing session.

Next we will digitize sections of the coastline of San Juan. Create another new shapefile layer as above: select `Layer>Create Layer> New Shapefile Layer`. In the dialog box that opens this time choose `Line` as the vector type and `1940_San_JuanCoastLine` as the file name. And make sure that the CRS is set to `EPSG: 3857 WGS 84 / Pseudo Mercator`.

Now when you toggle on editing and select the add features tool ![DigitizingExercise](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/Digitize19.png).  You will be digitizing line features.  As you click with the add features tool you can continue to add as many vertices to the line as you wish.  To complete the line segment, use the right mouse button.

Line features are more complex than the point features you made earlier and a few more considerations need to be made. One issue regards the shape of the coastline (or which ever type of feature you are digitizing as a line). You also must decide where to begin and end the individual line features.

Digitize the first feature using the add features tool ![DigitizingExercise](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/Digitize22.png). Be careful to keep each vertex as close to the coastline as possible.  The more vertices you add the smoother the coastline can be. To end the line segment `Right Click`.
![blank](https://github.com/brianhouse/mapping-architecture-urbanism-humanities/blob/master/Images/georef34.png)

Begin the next feature at the endpoint of the first and continue to digitize the coastline. You can experiment with digitizing other types of features on the map, and with digitizing features as a polygon layer.


## Part III: Making Shapefiles from Latitude Longitude coordinates

In the final part of this exercise you will learn to create a point feature class from a CSV file (a table) that contains latitude and longitude coordinates.

For the purposes of this exercise we will use a dataset of the [locations of hotels](https://data.pr.gov/en/Turismo/Mapa-de-los-hoteles-en-Puerto-Rico/k5ut-3ntx) in Puerto Rico that is collected and maintained by the Puerto Rican Planning Board.

To begin we will add this dataset to our map project using the `Add Delimited Text Layer` button (looks like a comma).

In the dialog box that opens use the `Browse` button to navigate to the `PR_Hotels.csv` file that is saved within the `Data/Tabular/`folder you downloaded with the github repository for this class.

Select `CSV` as the file format. `Point Coordinates` as the geometry definition. `Longitude` as the X field, and `Latitude` as the Y field.

Click `OK`

The point locations of Hotels should now appear on your map. To save this as a shapefile Right Click on the layer name in the layers panel and select `Save As`.

## Deliverables
To complete this tutorial, create a zip file containing your `1940_San_JuanCoastLine`,  `NamedBuildings_SanJuan` and `PR_Hotels` shapefiles (remember to include all of the files which comprise the shapefile format) as well as your GeoTiff of the 1940 USGS map and upload this to Canvas. 
______________________________________________________________________________________________________________


Tutorial adapted by Dare Brawley for *Conflict Urbanism: Puerto Rico Now* a seminar course taught at Columbia University in Spring 2019. Based on tutorial adapted by Michelle McSweeney for *Conflict Urbanism: InfraPolitics* a seminar course taught at Columbia University in Fall 2017 by the [Center for Spatial Research](http://c4sr.columbia.edu/). Originally written by Eric Glass, for *Mapping for the Urban Humanities*.
