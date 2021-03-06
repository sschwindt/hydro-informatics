Geodata
=======

.. tip::
   Use `QGIS <geo_software.html#QGIS>`__ to display geospatial data and to create maps in *PDF* or image formats (e.g., *tif*, *png*, *jpg*).

Geodata sources
---------------

Geospatial data can be retrieved for various purposes from different sources. Here are some of them:

-  Geographical, atlas map-like data are provided by    `naturalearthdata.com <https://www.naturalearthdata.com>`__ (e.g.,    with their 227-mb `Natural Earth quick start    kit <http://naciscdn.org/naturalearth/packages/Natural_Earth_quick_start.zip>`__).
-  Satellite imagery is available at 
  
	-   `USGS’ Earth Explorer <https://earthexplorer.usgs.gov/>`__.	  
	-   `eesa’s copernicus open access hub <https://scihub.copernicus.eu/dhus/#/home>`__ (Sentinel-2)	  
	-   `planet.com <https://www.planet.com/products/monitoring/>`__ (commercial)

-  `LiDAR <https://oceanservice.noaa.gov/facts/lidar.html>`__ data can be found at `opentopography.org <https://opentopography.org/>`__.
-  Climatological data are provided by `NASA Earth Observation <https://neo.sci.gsfc.nasa.gov/>`__.
-  Meteorological (e.g., temperature or precipitation) and real-time satellite data are available at `wunderground.com <https://www.wunderground.com/>`__ and its `wundermap <https://www.wunderground.com/wundermap>`__.
-  Data on land use (including canopy cover), socioeconomic characteristics, and global change are available at the `FAo    GeoNetwork <http://www.fao.org/geonetwork/srv/en/main.home>`__ or the archived ISCGM Global Map portal (`go to their github    archive <https://globalmaps.github.io/>`__).

Visualization
-------------

GIS software is needed to display geospatial data and many tools exist. This website primarily provides examples using `QGIS <geo_software.html#QGIS>`__. Since the use of GIS software, especially *QGIS*, is necessary in several places on the website, explanations on how to install *QGIS* are already included on the `Get Started > Geospatial software <geo_software.html>`__ page.

.. tip::
   The `BASEMENT pre-processing page <bm-pre.html>`__ features the basics of geospatial data handling with *QGIS*. Therefore, this introduction to numerical modeling is also a good introduction to *QGIS*.

.. _gdb:

Geodatabase
-----------

A geodatabase (also known as *spatial database*) can store, query (e.g., using `Structured Query Language SQL <https://en.wikibooks.org/wiki/Structured_Query_Language>`__), or modify data with geographic references (*geospatial data*). Primarily, geospatial data consist of vector data (see shapefiles), but raster data can also be implemented. A geodatabase links these data with attribute tables and geographic coordinates. The special aspect of geodatabases is that these data can be queried and manipulated by users via a (web or local) GIS (geographic information system) server. With software like `QGIS <geo_software.html#QGIS>`__ (or *ArcGIS Pro*), for example, queries can be made on a kind of local server using locally stored geodata. The typical geodatabase format is ``.gdb``, which works actually like a directory in *QGIS* or *ArcGIS*, and the maximum size of a ``.gdb`` file is 1 terabyte.

.. figure:: ../../img/geo-database.png
   :alt: gdb
   
   Functional skeleton of a geodatabase.

.. _vector:

Vector data
-----------

Vector data are visually smooth and efficient for overlay operations, especially regarding shape-driven geo-information such as roads or surface delineations. Vector data are typically less storage-intensive, easier to scale, and more compatible with relational environments. Common formats are ``.shp``, ``JSON`` or ``TIN``.

The shapefile format was invented by *Esri* (`download their PDf documentation <http://www.esri.com/library/whitepapers/pdfs/shapefile.pdf>`__)
and information contained in shapefiles can be:

-  Polygons (surface patches).
-  Points with x-y-z coordinates and an *m* field containing point data.
-  (Poly) lines consisting of lines defined by start points and 
   endpoints.

.. _shp:

Shapefile
~~~~~~~~~

.. note::
   The ``gdal.ogr`` driver name for shapefile handling is ``ogr.GetDriverByName('ESRI Shapefile')``. A shapefile is not just one file and consists of three essential parts: \* a ``.shp`` file, where geometries are stored, \* a ``.shx`` file, where indices of the geometries are stored, \* a ``.prj`` file that stores the projection, and \* a ``.dbf`` file containing attribute information (constitutes the attribute table).

These three files need to be in the same folder -  otherwise, the shapefile does not work. A couple of other files may occur when we manipulate a shapefile (e.g., ``.atx``, ``.sb*``, ``.shp.xml``, ``.cpg``, ``.mxs``, ``.ai*``, or ``.fb*``), but we can ignore those files.

Shapefile vector data typically has an attribute table (just like any other geodatabase) in which each polygon, line or point object can be assigned an attribute value. Attributes are defined by columns along with their names (column headers) and can have numeric (e.g., *float*, *double*, *int*, or *long*), text (*string*), or date/time (e.g. *yyyymmdd* or *HH:MM:SS*) formats.

.. figure:: ../../img/geo-shp-illu.png
   :alt: shapefile presentration
   
    Illustration of point, (poly) line, and polygon shapefiles.

Shapefile versus geodatabase
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A shapefile can be understood as a concurring format to a geodatabase.
Which file format is better? Strictly speaking, both a geodatabase and a shapefile can perform similar operations, but a shapefile requires more storage space to store similar contents, cannot store combinations of data and time, nor does it support raster files or *Null* (*not-a-number*) values. So basically we are better off with geodatabases, but the usage of shapefiles is popular and many geospatial operations focus on shapefile manipulations.

.. _tin:

Triangulated Irregular Network (TIN)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A triangulated irregular network (TIN) represents a surface consisting of multiple triangles. In hydraulic engineering and water resources research, one of the most important usage of TIN is the generation of computational meshes for numerical models (e.g., `on this website’s BASEMENT tutorial <bm-pre.html>`__). In such models, a TIN consists of lines and nodes forming georeferenced, three-dimensionally sloped triangles of the surface, which represent a digital elevation model (DEM). TIN nodes have georeferenced coordinates and potentially more attribute information such as node IDs and elevation. The advantage of a TIN DEM over a raster DEM is that it requires less storage space. Alas, manipulating a TIN is not that easy like manipulating a raster. The below figure shows an example TIN created with ```matplotlib.tri.TriAnalyzer`` <https://matplotlib.org/3.1.1/api/tri_api.html#matplotlib.tri.TriAnalyzer>`__), and based on a `showcase from the matplotlib docs <https://matplotlib.org/3.1.1/gallery/images_contours_and _fields/tricontour_smooth_delaunay.html#sphx-glr-gallery-images-contours-and -fields-tricontour-smooth-delaunay-py>`__.
The file ending of a TIN is ``.TIN``.

.. figure:: ../../img/geo-tin.png
   :alt: tin-illu
   
   Illustration of a TIN.

GeoJSOn
~~~~~~~

.. note::
   The ``gdal.ogr`` driver name for shapefile handling is ``ogr.GetDriverByName('GeoJSON')``.
`GeoJSON <https://geojson.org/>`__ is an open format for representing geographic data with simple feature access standards, where *JSON* denotes *JavaScript Object Orientation* (`read more about JSON file manipulation in the Python intro on this website <hypy_xml.html#json>`__). The *GeoJSON* file name ending is ``.geojson`` and a file typically has the following structure:

.. code:: json 

   {
     "type": "FeatureCollection",      "features": [
       {
         "type": "Feature",    "geometry": {
           "type": "Point",      "coordinates": [9.104028940200806, 48.74417005744522]
         },    "properties": {
           "name": "IWS"
         }
       }
     ]
   }

Visit `geojson.io <https://geojson.io/>`__ to build a customized *GeoJSON* file. While *GeoJSON* metadata can provide height information (``z`` values) as a ``properties`` value, there is a more suitable offspring to encode geospatial topology in the form of the still rather young `TopoJSON <https://github.com/topojson/topojson/wiki>`__ format.

.. _raster:

Gridded cell (raster) data
--------------------------

Raster datasets store pixel values (*cells*), which require large storage space, but have a simple structure. A big advantage of rasters is the possibility to perform powerful geospatial and statistical analyses. Common Raster datasets are, among others, ``.tif`` (*GeoTIFF*), *GRID* (a folder with a ``BND``, ``HDR``, ``STA``, ``VAT``, and other files), ``.flt`` (floating points), *ASCII* (American standard Code for Information Interchange), and many more image-like file types.

.. tip::
   Preferably use the `GeoTIFF <https://en.wikipedia.org/wiki/GeoTIFF>`__ format in raster analyses. A *GeoTIFF* file, typically includes a ``.tif`` file (with heavy data) and a ``.tfw`` (a six-line plain text world file containing georeference information) file.

.. note::
   The ``gdal`` driver name for *GeoTIFF* handling is ``gdal.GetDriverByName('GTiff')``.

.. figure:: ../../img/geo-raster-illu.png
   :alt: raster file illustration GeoTiff
   
   Illustration of the Natural Earth’s NE1_50M_SR_W.tif raster zoomed on Nepal, with point and line shapefiles indicating major cities and country borders, respectively. Take note of the tile-like appearance of the grid, where each tile corresponds to a 50m-x-50m raster cell.

.. _prj:

Projections and coordinate systems
----------------------------------

In geospatial data analyses, a projection represents an approach to flatten (a part of) the globe. In this flattening process, latitudinal (North/South) and longitudinal (West/East) coordinates of a location on the globe (three-dimensional *3D*) are projected into the coordinates of a two-dimensional (*2d*) map. When 3D coordinates are projected onto 2d coordinates, distortions occur and there is a variety of projection systems used in geospatial analyses. In practice this means that if we use geospatial data files with different projections, a distortion effect propagates in all subsequent calculations. It is absolutely crucial to avoid distortion effects by ensuring that the same projections and coordinate systems are applied to all geospatial data used. This starts with the creation of a new geospatial layer (e.g., a point vector shapefile) in *QGIS* and should be used consistently in all program codes. To specify a projection or coordinate system in *QGIS*, click on ``Project`` > ``Properties`` > ``CRS`` tab and select a ``COORDINATE_SYSTEM``. For example, an appropriate coordinate system for central Europe is ``ESRI:31493`` (read more in the `QGIS docs <https://docs.QGIS.org/testing/en/docs/user_manual/working_with_projections/working_with_projections.html>`__). Projected systems may vary with regions (*local coordinate systems*), which can, for example, be found at `epsg.io <https://epsg.io/>`__ or `spatialreference.org <https://spatialreference.org/>`__.

In **shapefiles**, information about the projection is stored in a ``.prj`` file (recall definitions in the `geospatial data section <#vector>`__), which is a plain text file. The Open Spatial Consortium (*OGC*) and *Esri* use `Well-Known Text (WKT) <http://docs.opengeospatial.org/is/18-010r7/18-010r7.html>`__ files for standard descriptions of coordinate systemsa and such a *WKT*-formatted ``.prj`` file can look like this:

.. code:: python 

   PROJCS["unknown",GEOGCS["GCS_unknown",
   DATUM["D_Unknown_based_on_GRS80_ellipsoid",SPHEROID["GRS_1980",6378137.0,298.257222101]],
   PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],
   PROJECTION["Lambert_Conformal_Conic"], PARAMETER["False_Easting",6561666.66666667], 
				..., UNIT["US survey foot",0.304800609601219]]

In `GeoJSON <#geojson>`__ files, the standard coordinate system is `WGS84 <https://www.unoosa.org/documents/pdf/icg/2018/icg13/wgd/wgd_12.pdf>`__ according to the `developer’s specifications <https://cran.r-project.org/web/packages/geojsonio/vignettes/geojson_spec.html>`__. The units and measures defined in the *WKT*-formatted ``.prj`` file also determine the units of *WK\ *\ **B** (*Well-Known Binary*) definitions of geometries such as line length (e.g., in meters, feet or many more), or polygon area (square meters, square kilometers, acres, and many more). 

.. tip::
   To ensure that all geometries are measures in meters and powers of meters, use `EPSG:3857 <https://spatialreference.org/ref/sr-org/6864/>`__ (former 900913 - g00glE) to define the *WKT*-formatted projection file.
