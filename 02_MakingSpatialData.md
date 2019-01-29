## Data in Space

This workshop will introduce participants to methods for creating data for historical GIS applications. The workshop will cover how to give geographic coordinates (georeference) scanned historical maps using QGIS, as well as how to digitize (trace) features from this scanned map to create new shapefiles. These are two key ways of creating spatial data from historical or other sources. Additional online tools for georeferencing scanned maps will also be introduced.

### Georeferencing a scanned paper map

#### Premise

In this exercise, you will explore some of the georeferencing tools available in QGIS and use them to georeference a 1902 map of the Bronx. You will learn how to use GIS tools to georectify raster datasets.  You will use the georeferenced map for the next exercise where you will digitize vector features from the map infomation. 

#### Notes on the data: 

The map you will be using for this exercise is one sheet of six from "Map or plan of that part of the Borough of the Bronx, City of New York, lying easterly of the Bronx River" published in 1902.  This map is from the Columbia Map collection and is an exceptionally detailed, large scale (1:7,200) series made shortly after the area east of the Bronx River was annexed from Westchester to the Bronx, and the Bronx was consolidated into New York City and New York County.  The library catalog record for the map can be found [here](https://clio.columbia.edu/catalog/9282162).  If you would like to see the entire map, there is another copy (in a lower resolution) in the New York Public Libraries digital collections [here](http://digitalcollections.nypl.org/items/dc910ee0-4682-0131-4759-58d385a7bbd0)

You are going to use [OpenStreetMap](https://www.openstreetmap.org/about) (OSM)  as reference data for the georeferencing process.  OSM provides a free, open-source map of the world from public domain and volunteered data.

#### Setting up QGIS

Open QGIS:

![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef1.png)

You are going to use OSM data as the reference data for the georeferencing process. You can view the OSM basemap service is QGIS through the OpenLayers plugin.  This plugin does not come pre-installed with QGIS, so you will probably need to add it.  Under the plugins menu, select “Manage and Install Plugins…” 
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef2.png)

The plugins dialog will open.  Search for “Openlayers Plugin.”  Highlight it, and click “Install plugin”:

![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef3.png)

It may take a few seconds to install.  Close the plugins menu when finished.  The OpenLayers tools should now appear under the Web menu: 

![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef4.png)

This plugin will allow you to view a number of basemap services and steam them directly into your QGIS workspace.  Choose the OpenStreetMap>OpenStreetMap option.
Since you are working in a new QGIS project, the map should show the entire earth as the default: 
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef5.png)
Use the zoom in tool ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef6.png) and zoom into the Central Bronx in the area around The Botanical Garden:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef7.png)
Now you will access the georeferencing tools and match the scanned map to the OSM map.  

Under the Raster menu, select Georeferencer>Georeferencer:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef8.png)

The Georeferencer screen will open:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef9.png)

Click on the Add Raster button ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef10a.png) and navigate to the JPEG image "Bronx1902Sheet2_Edit.jpg" from the class files in the directory MappingForTheUrbanHumanities-master\Class_Data\2_MakingData.  

It will appear in the georeferencer window:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef10b.png)

This map is one sheet of six of a map of the East Bronx in 1902.  This section represents the area around the New York Botanical Garden and the (then new) Bronx Zoo. Fordham University can be seen just to the southwest of the garden and the Norwood neighborhood is in the northeast corner.  The area to the east of the Bronx Park area is still largely undeveloped at this point.  

Historical maps can be difficult to georeference, and this sheet poses a number of complications.  The map projection is unclear and there are no ground control points or coordinates specified.  Because of this, you will georeference by matching physical features represented on the map with their current counterparts (and their known coordinates).  However, most of the features in this map have changed or no longer exist (or were never actually built in the first place).  Thus, you will need to be very careful to choose locations that you are confident match up well with their contemporary counterparts.   Fortunately, there are a number of good candidates, particularly on the western half of the map where many streets and buildings still exist in the same location.  You will use those to georeferenced the map.

The QGIS georeferencer does not allow you to view both the scanned map and the workspace at the same time, so you will have to inspect both maps in turn and choose carefully to select locations to add georeferencing control points. 
One candidate is the Haupt Conservatory in the Botanical Garden which continues to exist largely its original configuration.  Use the georeferencer zoom tools ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef11.png) to zoom to the conservatory structure in the southwest corner of the park: ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef12.png)
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef13.png)
 
Identify as precise a location as possible (a corner of the building will work nicely) and click on it in the georeferencing window using the add point tool ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef17.png) When you do so, the Enter map coordinates window appears:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef14.png)

If you knew the coordinates of this location, you could now add them manually, but since you do not, you must select them from the OSM data in the main QGIS window.  Click on the ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef15.png) button to see the QGIS workspace.  
You may want to use the QGIS zoom tools to zoom in very closely to the conservatory.
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef16.png)

Once you do so, you will need to reactivate the add button tool ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef17.png) by maximizing the georeferencing window and clicking the ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef18.png) button again.  Once you select the same location on the workspace window, you will automatically be brought back to the georeferencing window where the assigned coordinates will be imputed.  
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef19.png)

At this point, if you are dissatisfied, you can move the assigned control points with the move GCP point tool ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef20.png) or delete it entirely and start over with the delete point tool ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef21.png) 
If satisfied, click the OK button and the point will be assigned and appear on the map.  Also, a link table entry will be generated on the bottom of the window:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef22.png)

To add a second point, repeat the same process.  It is a good idea to choose another point in a different portion of the map.  A street intersection or corner from the western portion of the map will work well for this as most of those streets continue to exist in the same configuration.  
Here, I have zoomed in to the northwestern most potion of the map where I add a ground control point at the very center of the intersection of Gun Hill Road and Tryon Ave:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef23.png)

Repeat the same steps as used before to select the center of the same intersection from the OSM map and add the locations to the link table:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef24.png)

You will need to add a minimum of four points to complete the georeferencing (although more is generally better).  Generate at least two more points of your own choosing and add them to the link table.

Be careful to make sure that the control points you add do in fact match.  This can be quite tricky as many of the features have changed or were not actually built as planned.  

Normally it is a good idea to choose control points from throughout the map.  However, in this case this will be difficult as there are few features in the eastern sections of the map that can be reliably associated with contemporary locations.
In this example, I have selected six control points:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef25.png)

It is good practice to save the table of control points that you are building.  To do this, choose “Save GCP points as” under the file menu and save it in the .points format in the same location as the image. This will allow you to later recreate the work you have done:

![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef26.png)

Next, you will “transform” the image and create a georeferenced version of the scanned map image. In the georeferencer window, select transformation settings under the settings window:

![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef27.png)

Here you can select the transformation type (Polynomial 1 should be appropriate here), resampling method (Cubic is often used for resampled images and photos), output location and name, and the spatial reference system (here I have selected EPSG:3857, the pseudo Mercator projection used in the OSM data).  You can also opt to have the georeferenced layer added to QGIS when finished: 

![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef28.png)

Close the settings options and click on the start georeferencing button ![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef29.png).

After the transformation finishes, you should see the map appear in the QGIS workspace:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef30.png)

You can make the scanned map layer partially transparent in the layer properties.  Right click on the map in the layer panel and select properties:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef31.png)

On the left panel in the properties dialog, select Transparency, here you can adjust the global transparency with a slider: 
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef32.png)

Compare the georeferenced map with the Open Street Map layer.  Make sure that features appear to match up closely:
![blank](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/GeoRef33.png)

In the next portion of the exercise you will be using the sheet you georeferenced here and digitizing some of the features from it. 

###Digitizing Features from a georeferenced map

#### Premise

In this exercise, you will explore some of the on-screen hand digitizing tools available in QGIS and use them to digitize trees, paths and other features from a georeferenced map.  In essence, you will be converting raster spatial data into vector based features.

### Digitizing Exercise

Open QGIS:

![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize1.png)

Click on the add raster button ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize2.png) and navigate to the georeferenced image you made in the [Making Data 01](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/04_MakingData01.md) exercise.  Since you verified its accuracy already, you will not need any basemap data for this exercise:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize3.png)

This map is part of a very large-scale plan and the Bronx park area, which contains the then-new botanical garden and zoo, is particularly detailed.  Every structure, road, walking path, and tree is mapped.  In the next part of this exercise, you will create new vector datasets, and hand-digitize some of the path and tree features.

First you will digitize some trees.  For the trees you will use point geometry, so this will be a particularly simple dataset.

Remove any transparency from the georeferenced map layer. Zoom into the southwest corner of Bronx Park, where the Conservatory garden and library (labeled ‘museum’ on the map) are:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize4.png)

Next you will create a new point layer.  Under the layer menu, choose create new layer and new shapefile layer:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize5.png)

 In the new vector dialog layer, choose type “Point”.  You can also create additional attribute fields for your dataset, if applicable.  Here, I have added a tree “type” attribute and made it a text field with a maximum length of 80.  Select OK:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize6.png)

Save the new file in the same directory with your map, and name it BronxParkTrees.
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize7.png)

 The layer will now appear in the Layers panel:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize8.png)

Now begin editing by depressing the toggle editing tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize9.png) while the trees layer is highlighted in the layers panel.  Now you can use the add feature tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize10.png) to start creating trees.  Click on one of the trees in the map.  An attribute dialog appears where you can type in attribute information for the feature you just created:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize11.png)

There is no information on the map in regards to the type of tree; however, I know that the trees in front of the library are a stand of stately tulips, so I am entering that information now.  Click OK when finished. 

Continue to digitize trees in this corner of the park:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize12.png)

If you want to move one of the point features you can use the move feature tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize13.png) if you want to delete a tree, you can select it with the select features tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize14.png) at use the delete key on the keyboard.  It is a good idea to regularly use the “save for selected laters” function to save your work as you digitize:  
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize15.png)

When finished, depress the toggle editing tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize16.png) to close the editing session
Next you will digitize some of the park pathways.  Create another new shapefile layer as above, but this time choose “Line” as the vector type and BronxParkPaths as the file name:

![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize17.png)

![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize18.png)

Now when you toggle on editing and select the add features tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize19.png).  You will be digitizing line features.  As you click with the add features tool you can continue to add as many vertices to the line as you wish.  To complete the line segment, use the right mouse button. 

Line features are more complex than the point features you made earlier and a few more considerations need to be made. One issue regards the shape of the streets and paths.  Since these streets are so detailed you have the option of actually digitizing the curbs or path outlines.  Instead, you are going to digitize the ‘centerline,’ using a single line feature to represent the center of the path feature.  

You also must decide where to begin and end the individual line features.  A common practice is to create individual features between every intersection, ending each feature at the next intersection.  In this way, you can represent the connectivity of the features, essentially modeling a network.  It is important then to make sure that the connecting features are exactly coincident.  You can make sure that you connect features while digitizing by taking advantage of snapping tolerances.  Snapping tools will automatically adjust the digitizing tools and ‘snap’ them to specified features as the cursor gets sufficiently close. 

To set snapping, select “snapping options” under the settings menu: 
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize20.png)

Set the snapping options for the current layer to be within 10 map units of a vertex:
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize21.png)

Now the add feature tool will automatically snap to another feature’s vertex whenever the cursor comes within 10 meters.

Digitize the first feature using the add features tool ![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize22.png). Be careful to keep each vertex as close to the center of the street as possible.  The more vertices you add the smoother the street can be. Right click at the middle of the first intersection. 
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize23.png)

Begin the next feature at the endpoint of the first.  Make sure the first point ‘snaps’ to the last vertex.  In QGIS the cursor will highlight when you get within the snapping tolerance.
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize24.png)

Continue to digitize until the next intersection. 
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize25.png)

Continue to add paths in this section of the map.  Remember to regularly save your work.
![DigitizingExercise](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities/blob/master/Tutorials/Images/MakingData01/Digitize26.png)


###Additional QGIS Tutorial Resources Related to Making Data 
Also available as a stand-along resources page [here](https://github.com/CenterForSpatialResearch/Fall2017Workshops/blob/master/Resources/TutorialAndDataResources.md)

* **[Center for Spatial Research Tutorial Library](http://c4sr.columbia.edu/tutorials)**
	* [Geocoding coordinates and street addresses](https://github.com/CenterForSpatialResearch/MappingForTheUrbanHumanities_2017/blob/master/Tutorials/06_MakingData03.md)

* **[Programming Historian](https://programminghistorian.org/lessons/geocoding-qgis)**
	* [Geocoding Historical Data using QGIS](https://programminghistorian.org/lessons/geocoding-qgis)
		* this great tutorial covers how to create a custom gazetteer to geocode historical places


### A Few Resources for Researching Spatial Data

**Places to Start**

* Columbia University Libraries, specifically the [Research Data Services](http://library.columbia.edu/locations/dssc/data/service.html) (formerly, Digital Social Sciences Center), at Lehman Library:
	* The DSSC maintains the Columbia University [Spatial Data Catalog](https://geodata.library.columbia.edu) which lists all spatial data held by the Columbia Libraries
	* The DSSC also maintains research guides for how to find spatial data from other sources and libraries. 

### Digitized Map Collections

The following are a few links to major resources for researching digitized historic map collections.

**Places to Start**

* Columbia University Libraries, specifically the [Digital Social Sciences Center,](http://library.columbia.edu/services/research-data-services.html) at Lehman Library:
	* [GIS and Spatial Data Research Guide](http://guides.library.columbia.edu/c.php?g=715646&p=5092264)
	* The DSSC is the home of the [Lehman Map Collection](http://library.columbia.edu/locations/maps/about.html)
	* [GeoData @ Columbia](http://geodata.cul.columbia.edu) is a tool for searching Columbia's spatial data holdings including historical maps, by location. 

* Other University libraries often maintain listings of good online historical map resources

**Some Collections of Digitized Historical Maps**

* [David Ramsey Map Collection](http://www.davidrumsey.com)

* [Perry-Castañeda Library, Map Collection](http://www.lib.utexas.edu/maps/)

* [Norman B Leventhal Map Center](http://maps.bpl.org)

* [U.S. Library of Congress](https://www.loc.gov/maps/collections/)

* [Afriterra](http://www.afriterra.org)

* [Old Maps Online](http://www.oldmapsonline.org)

* [New York Public Library Map Division](https://www.nypl.org/blog/2014/03/28/open-access-maps)
	* Maps can be viewed through the [NYLP Digital Collections](http://digitalcollections.nypl.org/search/index?filters%5BphysicalLocation_mtxt_s%5D%5B%5D=Map+Division&keywords=&sort=dateDigitized_dt+desc)
	* or through the [NYPL Map Warper](http://maps.nypl.org/warper/)

______________________________________________________________________________________________________________

Tutorial adapted by Dare Brawley for the [Fall 2017 CSR Workshop Series](http://c4sr.columbia.edu/news/fall-2017-gis-workshops). Tutorial originally written by Eric Glass, for *Mapping for the Urban Humanities*, a intensive workshop for Columbia University faculty taught in Summer 2017 by the [Center for Spatial Research](http://c4sr.columbia.edu). More information about the course is available [here](http://c4sr.columbia.edu/courses/mapping-urban-humanities-summer-bootcamp).


