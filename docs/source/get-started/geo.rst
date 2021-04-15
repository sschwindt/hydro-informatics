
Geospatial Softtware
====================

Geospatial analyses (or analytics) use, manipulate and illustrate data from geographic information systems (GIS). GIS data contain geographically referenced and spatially explicit information of for example gauging stations, terrain elevation, or land use. Efficient processing of geospatial data involves programming methods, where *Python* is an efficient tool. This page presents desktop software for manual geospatial analyses and the illustration of geospatial data. For geospatial programming, please refer to the section `Pythongeospatial <geo-python.html>`__.

.. note::
   Geospatial data are either geographically referenced, pixel-based `rasters <https://en.wikipedia.org/wiki/Raster_graphics>`__ data or vector-based *Esri* `shapefiles <https://en.wikipedia.org/wiki/Shapefile>`__ (read more on the `Pythongeospatial <geospatial-data.html>`__ pages).

QGIS
----

For the visualization of geodata (``.shp`` and ``.tif`` files) a GIs software is required and the analyses described on these pages refer to the usage of `QGIS <https://www.QGIS.org>`__. This website uses *QGIS* within the sections on `geospatial programming with Python <geo-python.html>`__ and `numerical modelling with the ETh Zurich’s BASEMENT <basement.html>`__ software.

Install QGIS on Windows
~~~~~~~~~~~~~~~~~~~~~~~

Download and install the latest version of `QGIS <https://www.QGIS.org/en/site/forusers/download.html>`__ for Windows.

Install QGIS on Linux (via Flatpak)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The *QGIS* developers provide detailed installation instructions for several *Linux* distributions, but the instructions will not satisfy all requirement for the use of *QGIS* described on *hydro-informatics.github.io*. One of the most functional ways for installing *QGIS* on *Linux* is to use `Flatpak <https://flathub.org/apps/details/org.QGIS.QGIS>`__, which requires some system preparation. On *Debian*-based *Linux* platforms (e.g., all sorts of *Ubuntu* such as *Lubuntu* or *Mint*) open *Terminal* and tap (the second line is only needed if you use *GNOME*):

::

   sudo apt install flatpak    sudo apt install gnome-software-plugin-flatpak    flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo 

Restart the system and open the *Software Manager* app. It will update and add the flathub repo. Once the update was successful, search for *QGIS* and click *Install* (patience
-  the installation may take while).

The *QGIS Flatpak* installation will most likely not include the important *scipy* module. In order to fix this issue, open *Terminal* (stand ard Linux application) and type:
\ ``flatpak run --command =pip3 org.QGIS.QGIS install scipy --user`` 
This solution has been tested on *Linux Ubuntu* and *Linux Mint*. It potentially also works with *Red Hat*, *openSUSE*, *Mac OS*, *Arch*, *Fedora*, *and roid*, *Debian*, *Kubuntu* and many more (read installation guides on the `maintainer’s website <https://flatpak.org/setup/>`__). Read more about the *QGIS Flatpak* installation on the `QGIS website <https://QGIS.org/en/site/forusers/alldownloads.html#flatpak>`__.

Install QGIS on macOs
~~~~~~~~~~~~~~~~~~~~~

.. note::
   If you plan to use BASEMENT for numerical modelling: BASEMENT will not run on macOS.

Download and install the latest version of `QGIS <https://www.QGIS.org/en/site/forusers/download.html>`__ for macOS. The integrity of using macOS for the applications on *hydro-informatics.github.io* is has not yet been tested. Possible trouble-shooting with *Python* is provided by `kyngchaos.com <https://www.kyngchaos.com/software/QGIS/>`__.

Learn QGIS
~~~~~~~~~~

Working with geospatial data editors involves complex tasks that require background knowledge before intuitive comprehension is possible. The *QGIS* developers provide compound `tutorials on their website <https://docs.QGIS.org/testing/en/docs/training_manual/index.html>`__ (`also available in other languages including Czech, French, German, and 
Portuguese <https://www.QGIS.org/en/site/forusers/trainingmaterial/index.html>`__).
On this website, *QGIS* is occasionally used for plotting and creating georeferenced data (e.g., the chapters on `geospatial programming <geo-python.html>`__ and `numerical modelling BASEMENT <bm-pre.html>`__). These chapters illustrate the usage of *QGIS* with screenshots for specific tasks and do not cover a full tutorial for working with *QGIS*.

.. _basemap:

Basemaps for QGIS (google, open street maps and more)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. note::
   A fast internet connection is required for adding online base maps.

To add a base map (e.g., satellite data, streets, or administrative boundaries), go to the **Browser**, right-click on **XYZ Tiles**, select **New Connection…**, add a name and a URL of an online base map. Once the new connection is added, it can be added to a *QGIS* project by drag and drop just like any other geodata layer. The below figure illustrates the procedure of adding a new connection and its XYZ tiles as a layer to the project.

.. image:: ../img/QGIS-basemap.png
   :alt: basemap”	:caption: Add a base map to QGIS: (1) locate the Browser (2) right-click on XYZ-Tiles and select New Connection… (3) enter a Name and a URL (see below table)
for the new connection, click OK (4) drag and drop the new tile (here:
Google Satellite) into the Layers tab.

The following URL can be used for retrieving online XYZ tiles (more URLs can be found in the internet).

+------------+---------------------------------------------------------+
| Provider   | URL                                                     |
| (Layer     |                                                         |
| Name)      |                                                         |
+============+=========================================================+
| ESRI World | ``https://server.arcgisonline.com/ArcGIS/r              |
| Imagery    | est/services/World_Imagery/MapServer/tile/{z}/{y}/{x}`` |
+------------+---------------------------------------------------------+
| ESRI       | ``https://server.arcgisonline.com/ArcGIS/rest           |
| Street     | /services/World_Street_Map/MapServer/tile/{z}/{y}/{x}`` |
+------------+---------------------------------------------------------+
| ESRI Topo  | ``https://server.arcgisonline.com/ArcGIS/re             |
|            | st/services/World_Topo_Map/MapServer/tile/{z}/{y}/{x}`` |
+------------+---------------------------------------------------------+
| Google     | ``https://mt1.google.com/vt/lyrs=s&x={x}&y={y}&z={z}``  |
| Satellite  |                                                         |
+------------+---------------------------------------------------------+
| Google     | ``https://mt1.google.com/vt/lyrs=m&x={x}&y={y}&z={z}``  |
| Street     |                                                         |
+------------+---------------------------------------------------------+
| Ope        | ``http://tile.openstreetmap.org/{z}/{x}/{y}.png``       |
| nStreetMap |                                                         |
| (OSM)      |                                                         |
+------------+---------------------------------------------------------+
| OSM Black  | ``http://tiles.wmflabs.org/bw-mapnik/{z}/{x}/{y}.png``  |
| and White |                                                         |
+------------+---------------------------------------------------------+

.. tip::
   Most base maps are provided in the ``EPSG:3857 -WGS84 / Pseudo Mercator`` coordinate system (CRS). To use custom geodata products, make sure that all other layers have the same coordinate system. Read more about coordinate systems projections on the `geospatial data <geospatial-data.html#prj>`__ and `shapefile projection <geo-shp.html#prj-shp>`__ pages.

Install *QGIS* conda Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In `Anaconda Prompt <hy_ide.html#anaconda>`__, you can create a new environment to specifically use *QGIS* features (i.e., tools and scripts) including its raster calculator. The environment is featured by *Open Data Cube* (`read more <https://datacube-QGIS.readthedocs.io/en/latest/installation.html>`__) and can be installed as follows:

::

   conda create  -c conda-forge -n QGIScube python=3.6 QGIS=3 datacube    conda activate QGIScube 

Get Useful Plugins 
~~~~~~~~~~~~~~~~~~

The conversion between geospatial data types and numerical (computational) grids can be facilitated with plugins. To install any plugin in *QGIS*, go to the ``Plugins`` menu >
``Manage and Install Plugins...`` > ``All`` tab > ``Search...`` for a relevant plugin and install it.

In the context of river analysis, the following plugins are recommended and used at multiple places on this website:

-  The *Crayfish* plugin, which is available in the *QGIS* toolbox after the installation.

Enable the QGIS Toolbox 
~~~~~~~~~~~~~~~~~~~~~~~

Follow the below illustrated instructions to enable the *QGIS* *Toolbox*.

.. image:: ../img/QGIS-tbx.png
   :alt: enable QGIS toolbox”

   :caption: Open QGIS’ Toolbox window from the main menu.

.. _agis:

ArcGIS Pro
----------

.. important::
   ArcGIS Pro is designed for Windows and will not run on macOS or Linux. In addition, a license needs to be purchased. The proprietary software *ArcGIS Pro* represents a powerful tool for any kind of geospatial analysis including web applications. *ArcGIS Pro* is maintained by `esri <https://www.esri.com/>`__ and comes with an own `Python conda Environments <hypy_install.html>`__. With the focus on freely available software, the usage of *ArcGIS Pro* and its *Python* environment including the ``arcpy`` package is just mentioned on this website.

Others 
------

There are many other tools for geospatial analyses, which all deserve much more than just being mentioned here. Alas, for practical reasons, this website focuses on the usage of *QGIS*. This is why there is just a absolutely-not-complete list of other GIS tools here:

-  `SAGA (System for Automated Geoscientific    Analyses) <http://www.saga-gis.org/en/index.html>`__
-   `Mapline <https://mapline.com/>`__
-   `Mapbox <https://www.mapbox.com/>`__
-   `uDig <http://udig.refractions.net/>`__ 

Geospatial analyses
-------------------

Geospatial analyses involve efficient code practices (e.g., with *Python*) and this is why detailed descriptions of geospatial data handling are embedded in the `Pythongeospatial <geo-python.html>`__ chapter of this website.
