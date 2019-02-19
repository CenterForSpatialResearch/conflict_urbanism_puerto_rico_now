# Working with Satellite Imagery

This exercise will introduce you to multispectral satellite imagery, and to the process of visualizing phenomena through 'false color composites'. As an introduction we will create false color composites using Landsat satellite imagery of Puerto Rico captured just before and after Hurricane Maria.

After completing this exercise you will:
* have familiarity with basic characteristics of multispectral satellite imagery
* learned how to acquire Landsat satellite imagery through the U.S. Geological Survey
* created a false color composite from multispectral Landsat dataset

## Some Background on Working with Landsat Satellite Imagery

In order to explore characteristics of multispectral satellite imagery we will download a multispectral image from the USGS and experiment with creating images known as 'false color composites.'

In order to do this we first will introduce some key ideas about multispectral satellite imagery and the Landsat satellite in particular.

**Multispectral** satellite imagery refers to a type of data that records specific wavelength ranges in the electromagnetic spectrum. In the case of the Landsat program, the Landsat Satellite has  sensors that are able to detect light waves beyond the [visible light spectrum](https://en.wikipedia.org/wiki/Visible_spectrum) (both near infrared as well as ultra violet frequencies). Specific frequency ranges are each recorded in a distinct **band**.

A single Landsat 'image' is actually composed of multiple bands. Each band is an individual **raster** dataset where the value of each pixel corresponds to the wavelength of reflected light captured by the satellite. These datasets are stored as individual `.tif` files which appear as monochromatic images when we load them in QGIS individually.

For example the image below show band 5 from a Landsat 8 satellite image captured of the western portion of Puerto Rico on October 3, 2017:
![monochrome](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite12.png)

This image shows wavelengths along the electromagnetic spectrum as well as the ranges that are captured by each Landsat band.  
![spectrum](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/Landsat8_SpectralBands.jpg)

The field of remote sensing science is dedicated, in part, to understanding the different 'spectral signatures' of features on the earth's surface. In other words, what frequencies of light in the electromagnetic spectrum do various types of vegetation reflect? Do certain types of man-made surfaces reflect more ultra violet light? Does healthy vegetation reflect greater or less light in the near infrared range than vegetation in drought conditions?

From the answers to these questions researchers study topics like landscape change, [ecological vulnerability](https://landsat.visibleearth.nasa.gov/view.php?id=88873), and large scale [urban development](https://www.wired.com/2012/07/landsat-city-change/).

One of the ways that remote sensing scientists study these 'spectral signatures' is through creating color composite images using multiple of the monochromatic bands from multispectral imagery. This is a method by which each band is assigned a color (red, green, or blue) and its values are mapped onto an RGB color scale. We can make color composites that approximate a 'natural color' image of the earth's surface. Or we can combine different frequency ranges from the electro magnetic spectrum into **false color composites** to reveal different phenomena on the ground.
Below shows natural color and 'near infrared' false color composite images:
![compare](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite13.png)

[This introduction](https://fromgistors.blogspot.com/p/user-manual.html) to remote sensing written by the developer of a remote sensing library for QGIS that we will use in this exercise provides a good entry point to further information on many of these concepts.

Students in this seminar might be interested in using Landsat satellite imagery as a base map for other analysis, or as an illustration of change over time in a particular area of the island.

The Landsat satellite circles the globe on a 16 day cycle. [This page](https://landsat.usgs.gov/landsat_acq) from the USGS is helpful for identifying the days of coverage for a particular area. From it we can see that the western portion of Puerto Rico is falls between two paths of the landsat's orbit: the western portion of the island is captured on Day 1 of the cycle, and the easter portion is captured on the 10th day of the cycle.

This exercise will walk through how to download Landsat data and then how to perform basic tasks with it in QGIS.

## Downloading Landsat satellite images

Landsat satellite data is freely available and can be downloaded via a number of different websites. We will be using the USGS website: [EarthExplorer](https://earthexplorer.usgs.gov/)

1. Select `Register` and then follow steps to **Register for an EarthExplorer account**
2. Use the map to zoom in to Puerto Rico (or your area of interest)
3. In the `Coordinates` box select the `Use Map` button. Coordinates around the area you are viewing will populate into this menu.
![coordinates](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite001.png)
4. Select the date range you are interested in, for this example we are searching for images between **9/15/2017** and **10/15/2017**
5. Click through to `Data Sets`
6. In the `Data Sets` menu open the nested section for `Landsat` and then for `Landsat Collection 1 Level-1`
7. Check the box next to `Landsat 8 OLI/TIRS c1 Level-1`
![datasets](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite002.png)
8. Select `Additional Criteria` we will not make any selections here in this exercise, but note for future reference that you can use this to search only for images with less than a certain percentage of cloud cover.
9. Select `Results`. You should see a number of images for specified dates and paths. Here you can view the footprint of each image. As well as select images for download.

10. Find the images you are interested in downloading.
  - For this exercise select the images with the following attributes:
  Image 1:  
    Acquisition Date: 17-SEP-17  
    Path: 5  
    Row: 47  
  Image 2:  
    Acquisition Date: 03-OCT-17  
    Path: 5  
    Row: 47  
11. Click on the download icon (looks like a hard drive and a green arrow) for the first image.
12. In the Download Options menu that will open, select `Level -1 GeoTIFF Data Product`. This is the data set that will include all of the Landsat 8 multispectral bands discussed previously.
![download](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite003.png)
13. Repeat steps 11 and 12 to download the second image.
14. Two zip files will download, unzip them, and save in the working directory you are using for this class.

## Creating False Color Composites

We will use a tool called the "Semi-Automatic Classification Plugin" (SCP) to assist us with creating composite images from the bands of the Landsat images we just downloaded. This plugin has been developed by Luca Congedo and is released under the "Creative Commons Attribution-ShareAlike 4.0 International License." It is an example of the kind of open source tools being developed by the QGIS community.

Full documentation as well as related resources for this set of tools can be found [here](https://fromgistors.blogspot.com/p/semi-automatic-classification-plugin.html).

The SCP plugin provides a number of tools related to satellite image processing and analysis.

#### First we will **Install Semi-Automatic Classification Plugin**
1. Navigate to the `Plugins>Manage and Install Plugins` from your menu bar.
2. Search for and install the `Semi-Automatic Classification Plugin`
3. When the plugin has finished installing make sure the check box next to the plugin's name is checked and select `Close`.
![install](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/Satellite01.png)
4. A new toolbar and dock should have been added to your QGIS window. The are highlighted below in magenta. If these did not open for you, right click anywhere inside one of the grey toolbars surrounding the map canvas and select `SCP Dock` in the panels section, and `SCP Tools` and `SCP toolbar` in the toolbars section.
**Note: if you encounter any difficulty downloading or operating the Semi-Automatic Classification Plugin that you are not able to troubleshoot on your own please use one of the computer labs on campus to complete the tutorial.**
  - **The plugin is functioning normally on the large computer workstations in the International Affairs Building (Lehman Library).**
  - **GSAPP students can also use the computers in 202 Fayerweather Hall**

![dock](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite02.png)


#### Next we will load the Landsat data we just downloaded and **create a "Band Set"** to make color composites from this data.
1. Select the `Preprocessing` tool from the SCP toolbar.
![Preprocessing](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite03.png)
2. Click on the `Open` button and navigate to the directory containing the Landsat bands you want to work with. (Choose the folder containing the September 17 Landsat image bundle).
3. You'll notice that after you select this folder the metadata section of this dialog box will be populated.
![Bandlist](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite04.png)
4. In the list of Bands that appears below the metadata heading select bands 1, 8, 9, 10, 11, and BQA by clicking the number next to the band name. (You may need to expand the Band column in the table to see the band numbers).
5. Click the minus icon to remove these bands from the list.
    - **Note:** you should just have bands 2, 3, 4, 5, 6, 7 remaining in this list. Make sure you have no other bands.
6. Select:
    - `Apply DOS1 atmospheric correction`
    - `Create Band set and use Band set tools`
    -  `Use NoData value`  
    Your dialog box options should look like this:
![loading](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite06.png)
7. Click `Run` (the gear in the bottom right corner).
8. You will be prompted to choose a folder to save the new band set in. Create a new folder and name it `20170917_Converted` The tool will run and will take some time to complete. When it finishes (this may take a few minutes, this is a good time to take a break) all of the individual bands will appear in the layers panel.
9. We now need to **define our Band Set**. First, select the `Band set` icon.
    - In the band list select `refresh` to load all of the bands.
    - Select bands 2-7. Click the `Add band to band set` button (the plus sign). These bands should appear in the band set definition below.
    - select:
      - Quick wavelength settings as `Landsat 8 OLI [bands 2,3,4,5,6,7]`
      - `Create virtual raster of band set`
      ![bandsetdefinition](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite07.png)
10. Select the Band set layer as the `Input image` in the SCP Dock.
    - *note* you may need to click the refresh icon next to the input image dropdown menu
![Input](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite05.png)

11. Next, on the `SCP Toolbar` use the `RBG` tool *(highlighted below in magenta)* to set your desired band combination.

![RGB](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite08.png)

This tool tells the program which band it should map to the red, green, or blue band of a standard RBG image. Setting band 3 and Red, band 2, as Blue, and band 1 as Green will show a `natural color` image whose colors are similar to what we are familiar with. This combination is similar to what we see with the naked eye because it uses the bands that capture electromagnetic wavelengths in the visible light spectrum.

Further information about band combinations and the kinds of phenomena they make visible can be found [here](http://web.pdx.edu/~emch/ip1/bandcombinations.html). Take a look through this webpage and try out combinations that are interesting to you.



A color composite using `3-2-1` for a 'natural color' image:  

![natural](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite09.png)

The combination of bands `4-5-3` is particularly well suited for looking at land/water boundaries as well as levels of water saturation.

![435](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite14.png)

Or to view a 'near infrared' image set the RGB band values to `4-3-2`. This type of 'false color composite' image is similar to infrared aerial photography and highlights vegetation in shades of red. Try these and others.

![infrared](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite10.png)


12. To export a false color composite as a GeoTiff image (that freezes the given false color composite you've chosen) right click on the virtual raster that contains your `band set` in the layers menu. Select `save as` and choose `rendered image` as your output mode, and select a location and file name to save the image. This false color composite is now saved, you no longer have access to the raw data of each of the Landsat bands that originally comprised it but you can work with it as a base map or for other uses.

#### Repeat steps 1-12 on the second Landsat image bundle we downloaded to compare false color composites before and after Hurricane Maria.

The `4-5-3` combination which uses the near infrared, mid infrared, and red bands  highlights outflows and flooding in areas quite well, below is the same area depicted in the September 17 image above, but was captured on October 3, 2017:

![infrared](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite15.png)

### Deliverables:
Upload two color composite GeoTiff files to canvas.  

You can choose to upload one for each Landsat dataset we downloaded (September 17 and October 3, 2017), or two different composites for the same date, or download additional Landsat images for two different dates that interest you and create color composites for these.


If you are interested in learning how to make land use classifications based on Landsat satellite imagery you can follow [this](https://pointsunknown.nyc/tutorials/05_ChangeMapping.html#classification) tutorial written by CSR Research Scholar Grga Basic for *Points Unknown*.
_________________________________________________________________________________________________

Tutorial written by Dare Brawley, for *Conflict Urbanism: Puerto Rico Now*, a spring 2019 seminar offered by the [Center for Spatial Research](http://c4sr.columbia.edu) (With thanks to Grga Basic for guidance on working with Landsat imagery in QGIS). More information about the course is available [here](http://c4sr.columbia.edu/courses/conflict-urbanism-puerto-rico-now).
