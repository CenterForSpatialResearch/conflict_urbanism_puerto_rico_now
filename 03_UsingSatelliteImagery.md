## Working with Satellite Imagery

This exercise will introduce two types of remotely sensed data, multispectral satellite imagery, and high resolution natural color satellite and aerial imagery. In particular we will work with multispectral imagery from the Landsat Satellite Program and high resolution aerial and satellite images from Google Maps.

After completing this exercise you will:
* have familiarity with basic characteristics of multispectral satellite imagery
* learned how to acquire Landsat satellite imagery through the U.S. Geological Survey
* created a false color composite from multispectral Landsat dataset
* develop familiarity with the Google Static Maps API and download ungeoreferenced satellite and aerial imagery for a set of locations

### Working with Landsat Satellite Imagery

In order to explore characteristics of multispectral satellite imagery we will download a multispectral image from the USGS and experiment with creating images known as 'false color composites.'

In order to do this we first will introduce some key ideas about multispectral satellite imagery and the Landsat satellite in particular.

**Multispectral** satellite imagery refers to a type of data that records specific wavelength ranges in the electromagnetic spectrum. In the case of the Landsat program, the Landsat Satellite has  sensors that are able to detect light from frequencies beyond the (visible light spectrum)[https://en.wikipedia.org/wiki/Visible_spectrum] (both near infrared as well as ultra violet frequencies). Specific frequency ranges are each recorded in a distinct **band**. A single Landsat 'image' is actually composed of multiple `.tif` files, one for each band of data. Each of these bands is a monochromatic image.

This image shows wavelengths along the electromagnetic spectrum as well as the ranges that are captured by each Landsat band.  
![spectrum](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/Landsat8_SpectralBands.jpg)

The field of remote sensing science is dedicated, in part, to understanding the different 'spectral signatures' of features on the earth's surface. In other words, what frequencies of light in the electromagnetic spectrum do various types of vegetation reflect? Do certain types of man-made surfaces reflect more ultra violet light? Does healthy vegetation reflect greater or less light in the near infrared range than vegetation in drought conditions?

From the answers to these questions researchers study topics like landscape change, [ecological vulnerability](https://landsat.visibleearth.nasa.gov/view.php?id=88873), and large scale [urban development](https://www.wired.com/2012/07/landsat-city-change/).

One of the ways that remote sensing scientists study these 'spectral signatures' is through creating color composite images using multiple of the monochromatic bands from multispectral imagery. This is a method by which each band is assigned a color (red, green, or blue) and its values are mapped onto an RGB color scale. We can make color composites that approximate a 'natural color' image of the earth's surface. Or we can combine different frequency ranges from the electro magnetic spectrum into **false color composites** to reveal different phenomena on the ground.

[This introduction](https://fromgistors.blogspot.com/p/user-manual.html) to remote sensing written by the developer of a remote sensing library for QGIS that we will use in this exercise provides a good entry point to further information on many of these concepts.

Students in this seminar might be interested in using Landsat satellite imagery as a base map for other analysis, or as an illustration of change over time in a particular area of the island.

The Landsat satellite circles the globe on a 16 day cycle. [This page](https://landsat.usgs.gov/landsat_acq) from the USGS is helpful for identifying the days of coverage for a particular area. From it we can see that the western portion of Puerto Rico is falls between two paths of the landsat's orbit: the western portion of the island is captured on Day 1 of the cycle, and the easter portion is captured on the 10th day of the cycle.

This exercise will walk through how to download Landsat data and then how to perform basic tasks with it in QGIS.

#### Downloading Landsat satellite images

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
8. Select `Additional Criteria` we will not make any selections here but yuo can use this to search only for images with less than a certain percent of cloud cover.
9. Select `Results`. You should see a number of images for specified dates and paths.

Here you can view the footprint of each image. As well as select images for download.
10. Select the images you are interested in downloading.
  - For this exercise select the images with the following attributes:
  Image 1:
    Acquisition Date: 17-SEP-17
    Path: 5
    Row: 47
  Image 2:
    Acquisition Date: 03-OCT-17
    Path: 5
    Row: 47
11. Click on the download icon (looks like a harddrive) for each image.
12. In the Download Options menu that will open, select `Level -1 GeoTIFF Data Product`. This is the data set that will include all of the Landsat 8 multispectral bands discussed previously.
![download](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite003.png)
13. Repeat steps 11 and 12 to download the second image.
14. Two zip files will download, unzip them, and save in the working directory you are using for this class.

#### Creating False Color Composites

We will use a tool called the "Semi-Automatic Classification Plugin" (SCP) to assist us with creating composite images from the bands of the Landsat images we just downloaded. This plugin has been developed by Luca Congedo and is released under the "Creative Commons Attribution-ShareAlike 4.0 International License." It is an example of the kind of open source tools being developed by the QGIS community.

Full documentation as well as related resources for this set of tools can be found [here](https://fromgistors.blogspot.com/p/semi-automatic-classification-plugin.html).

The SCP plugin provides a number of tools related to satellite image processing and analysis.

First we will **Install Semi-Automatic Classification Plugin**
1. Navigate to the `Plugins>Manage and Install Plugins` from your menu bar.
2. Search for and install the `Semi-Automatic Classification Plugin`
3. When the plugin has finished installing make sure the check box next to the plugin's name is checked and select `Close`.
![install](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/Satellite01.png)
4. A new toolbar and dock should have been added to your QGIS window.
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
9. We now need to **define our Band Set**. select the `Band set` icon.
  - In the band list select `refresh` to load all of the bands.
  - Select bands 2-7. Click the `Add band to band set` button (the plus sign). These bands should appear in the band set definition below.
  - select:
    - Quick wavelength settings as `Landsat 8 OLI [bands 2,3,4,5,6,7]`
    - `Create virtual raster of band set`
    ![bandsetdefinition](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite07.png)
10. Select the Band set layer as the `Input image` in the SCP Dock.
  - *note* you may need to click the refresh icon next to the input image dropdown menu
![Input](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite05.png)
11. Use the `RBG` tool to set different band combinations. Look [here](http://web.pdx.edu/~emch/ip1/bandcombinations.html) for different combinations and the kinds of phenomena that they make visible.
![RGB](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite08.png)
- `3-2-1` will show a 'natural color' image
![natural](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite09.png)
- `4-3-2` will show a 'near infrared' image which highlights turbidity and silt in water in cyan and shows vegetation in shades of red.
![infrared](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite10.png)

#### Repeat steps 1-11 on the second Landsat image bundle we downloaded to compare false color composites before and after Hurricane Maria.

The near infrared band combination highlights outflows and flooding in areas quite well, below is the same area depicted in the September 17 image above, but was captured on October 3, 2017:
![infrared](https://github.com/CenterForSpatialResearch/ConflictUrbanismPuertoRicoNow_Tutorials/blob/master/Images/satellite11.png)
