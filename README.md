# ArcGIS to Google Earth Engine
For ArcGIS users looking to make the not-so-subtle leap to Google Earth Engine

## Objective:
The beauty of Google Earth Engine (GEE) is fundamentally tied to scale and near instant access to massive satellite imagery data. This clicked for me in particular from seeing analogous processes struggle to run and oftentimes crash in ArcGIS. As such, this document will provide an overview of the GEE working environment and relate its functionality back to ArcGIS through some examples. My aim is for you to see both the incredible upside, some of the quirks of a powerful geospatial tool built by computer scientists, and its current limitations.

## Data Types:
As in any coding language, data types are essential to knowing what one can do. GEE is no exception and contains all the typical data types (e.g. float, string, integers, lists, dictionaries, etc.), however, the power of GEE is scaled geospatial data manipulations so for starters, a primer on the essential data types are highlighted below to translate ArcGIS knowledge into GEE-space.
### Rasters
In GEE, rasters are called either an `Image` or `Image Collection`. The former is a single image, while the latter is any group of images. This “group” is rather flexible in that one can create a large stack of imagery for the same region of interest (ROI) over time, a collection of images in different ROIs that are not connected in any way, or some hybrid of the two. The key difference between an Image and Image Collection to note is that although both are imagery data like TIFF’s in ArcGIS, they are slightly different data types so must be treated differently when performing analysis on them. For example, the `.clip()` function only exists for the Image data type, so if one wants to do this for the all the images in an Image Collection, one needs to build a simple for loop to apply it. We’ll walk through some of these examples.
### Vectors
Vector data analysis of points, lines, & polygons is a relatively new capability for GEE announced at the GEE User Conference in June, 2017. As expected, the functionality for the data are more limited than GEE's origins with imagery.

Vector data in GEE follow GeoJSON nomenclature. So these can be geometries in the form of a `Point`, `LineString`, `Polygon`, `MultiPoint`, `MultiLineString`, and `MultiPolygon`. More thorough descriptions are always kept up to date [here](http://geojson.org) from the GeoJSON gods, but one can think of all these options as just different kinds of `shapefiles`, e.g. a point, line, or polgyon `feature class` in ArcGIS.

For our purposes, the all these geometry formats can fall into 2 primary categories: a `Feature` or `Feature Collection`. In similar fashion to GEE imagery formatting, a single vector geometry is a `Feature` whereas a group of features aggregate to a `Feature Collection`. Once again, the key functional distinction is that depending on which data type space you are in, you are able to access different parts of the GEE library. For example, the `.buffer()` function only exists for `Feature` data types so if one wants to buffer a bunch of features, a simple buffer function needs to be built before applying it all said features.

## Working Environment:
What is most likely the steepest learning curve for Arc-users making the jump to GEE is using the `Javascript Playground`. Although it looks rather simplistic, there is quite a bit of useful nuance the further we dive in so use this screenshot below for reference as we'll be coming back to its labels quite often.

![alt](../master/images/gee_working_env.png?raw=true "GEE Working Environment")

## Where to find help:
There are two main places to look if one cannot debug an issue or figure out a needed code sequence based on available documentation in the `Javascript Playground`.

1.) [The Google Earth Engine Developer's Guide](https://developers.google.com/earth-engine/): this is a fantastic resource that provides both commentary and sample code chunks to work through. There is almost too much to work through so the Search Bar is quite helpful here if you have specific need. Keep in mind, though, that this is primarily to get someone off the ground so the code samples are not terribly in depth spatial analyses since their function are too demonstrate technical features.

2.) [The Google Earth Engine Developers Google Group](https://groups.google.com/forum/#!forum/google-earth-engine-developers): you'll need to request for permissions, but this is where the bleeding edge of all things Earth Engine occurs. It's fantastic for posting questions, but also searching the archive for answers to challenges that others have previously faced. Think of this as the Earth Engine-Stackoverflow. One of my personal favorite things on the forums is to see the unveliebly creative scripts posted to achieve custom analyses. I highly recommend leaning on this more & more after getting comfortable with the basics as I've learned more from working through other folks' scripts than anything else.

## Sample Scripts:
I'll update this list to make it a more progressive learning curve, but here are a few to start checking out.

* [Tasseled Cap Transformation for Landsat-7 Scene in NC](https://code.earthengine.google.com/f209da7cfda9abee4b56967bec20d6de)

* [Temporal NDVI User-Interface at HUC12 Watershed level in Appalachia](https://code.earthengine.google.com/d57044ac966ccf89116a05ff8f99f870)
