Geospatial Libraries
====================

This page lists open-source packages for geospatial file manipulation with *Python*. The necessary packages are already installed if you use the provided ```hypy`` <hypy_install.html#create-and -install-conda-environments>`__ environment. The following sections provide explanations of relevant and optional packages for this course and how those can be installed.

.. admonition::

   The proprietary license-requiring ``arcpy`` package is described on the `Commercial software <geo-arcpy.html>`__ page.

.. _gdal:

gdal (including ogr and osr)
----------------------------

```gdal`` <https://gdal.org/>`__ and ``ogr`` of the `OSGeo Project <http://www.osgeo.org/>`__ stem from the *GDAL* project, which is part of the Open Source Geospatial Foundation (`OSGeo <https://www.osgeo.org>`__) -  the developers of *QGIS*. ``gdal`` provides many methods to convert geospatial data (file types, projections, derive geometries), where ``gdal`` itself hand els `raster data <geospatial-data.html#raster>`__ and its ``ogr`` module hand les `vector data <geospatial-data.html#vector>`__. The tutorials on this website depend on ``gdal`` and ``ogr`` (including ``osr`` for spatial referencing); so it is important to get the installation of ``gdal`` right.

To install ``gdal`` for *Python*, open `Anaconda Prompt <hypy_install.html#install-pckg>`__ and type:

.. code:: python 

   conda install -c conda-forge gdal 

.. tip::
   **Conda users** may experience that installing ``gdal`` results in conflicts. Wait for *Anaconda Prompt* resolving the conflicts, then type ``conda update conda``, ``conda update anaconda``, and restart *Anaconda Prompt*. Now re-install ``gdal`` with ``conda install -c conda-forge gdal`` (a similar procedure may be required for other geospatial package installations).

.. note::
   **None-conda users**, if you **cannot ``import gdal``**, for some apparently arbitrary reasons (e.g., ``Error: Arbitrary-like stuff is missing.``), the problem probably lies in the definition of environmental variables. The problem can be trouble-shot in *PyCharm* with the following solution 
   
   1. Go to *File* > *Settings …* > *Build, Execution, Deployment* > *Console* > *Python Console* > *Environment variables* 
   2. Set the following ``environment_variables``\ 
	``setx GDAL_DATA 'C:\Program Files\GDAL\gdal-data'``\ 
	``setx GDAL_DRIVER_PATH 'C:\Program Files\GDAL\gdalplugins'``\ 
	``setx PROJ_LIB 'C:\Program Files\GDAL\projlib'``\ 
	``setx PYTHONPATH 'C:\Program Files\GDAL\'``\  
	Wait a couple of moments until *PyCharm* adapted (*building skeleton …*) the new ``environment_variables`` and ``import gdal`` -  should work now.

.. admonition:: Linux

   In general, the installation of ``gdal`` in only an environment can be *tricky*. Therefore, *Linux* users may want to make a global installation with: 
   
   1. ``sudo apt install -y build-essentiallibxml2-dev libxslt1-dev`` (install build and *XML* tools) 
   2. ``sudo apt install libgdal-dev`` (install ``gdal`` development files) 
   3. ``sudo apt install python-gdal`` (install ``gdal`` itself) 
   4. Enable ``gdal`` in a virtual environment:
	-  run virtual wrapper:	``toggleglobalsitepackages``
	-  activate environment with ``conda activate ENVIRONMENT``
	-  activate global site packages for the current environment: ``toggleglobalsitepackages enable global site-packages`` 


geojson 
-------

```geojson`` <https://pypi.org/project/geojson/>`__ is the most direct option for handling `GeoJSON <geospatial-data.html#geojson>`__ data. To install ``geojson`` for *Python*, open `Anaconda Prompt <hypy_install.html#install-pckg>`__ and type:

.. code:: python 

   conda install -c conda-forge geojson 

descartes 
---------

Even though of proprietary origin, the ```descartes`` <https://docs.descarteslabs.com/api.html>`__ package (developed and maintained by `Descartes Labs <https://www.descarteslabs.com/>`__) comes with many open-sourced functions. Moreover, *Decartes Labs* hosts the showcase platform `GeoVisual Search <https://search.descarteslabs.com/>`__ with juicy illustrations of aritificial intelligence (*AI*) applications in geoscience. To install ``descartes`` for *Python*, open `Anaconda Prompt <hypy_install.html#install-pckg>`__ and type:

.. code:: python 

   conda install -c conda-forge descartes 

Python Imaging Library (PIL) / *pillow* 
---------------------------------------

Processing images with *Python* is enabled with the *Python Imaging Library* (*PIL*). *PIL* supports many image file formats, and has efficient graphics processing capabilities. The ``pillow`` library is a user-friendly *PIL* fork and provides ``Image*`` modules (e.g., ``Image``, ``ImageDraw``, ``ImageMath``, and many more).

The comprehensive ``pillow`` documentation is available at `readthedocs.io <https://pillow.readthedocs.io/en/stable/>`__. To install ``pillow`` in a *conda* environment open `Anaconda Prompt <hypy_install.html#install-pckg>`__ and type:

.. code:: python 

   conda install -c anaconda pillow 

shapely 
-------

A preferable and very well documented package for `shapefile <geospatial-data.html#shp>`__ handling is ```shapely`` <https://shapely.readthedocs.io/>`__. To install ``shapely`` for *Python*, open `Anaconda Prompt <hypy_install.html#install-pckg>`__ and type:

.. code:: python 

   conda install -c conda-forge shapely 

``shapely`` is also used in the ```geo_utils`` package <https://geo-utils.readthedocs.io/>`__, which contains tailored functions for this course.

pyshp 
-----

Another shapfile handling package ```pyshp`` <https://pypi.org/project/pyshp/>`__, which provides pure *Python* code (rather than wrappers), which simplifies direct dealing with shapefiles in *Python*. To install ``pyshp`` for *Python*, open `Anaconda Prompt <hypy_install.html#install-pckg>`__ and type:

.. code:: python 

   conda install -c conda-forge pyshp 

.. _other:

Other packages
--------------

Besides the above mentioned packages there are other useful libraries for geospatial analyses in *Python* . **Packages in bold font** are used in the ```geo_utils`` package <https://geo-utils.readthedocs.io/>`__, which contains tailored functions for this course.

-  ```alphashape`` <https://pypi.org/project/alphashape/>`__ creates    bounding polygons containing a set of points install in *Anaconda Prompt* with \ ``conda install -c conda-forge alphashape``).
-  ```django`` <https://docs.djangoproject.com/en/3.0/ref/contrib/gis/>`__ as a geographic web frame and for database connections - install in *Anaconda Prompt* with \ ``conda install -c anaconda django``
-   ```geopand as`` <https://geopand as.org/>`__ enables the application of *pandas* data frame operations to geospatial datasets -  install in    *Anaconda Prompt* with \ ``conda install -c conda-forge geopand as``
-   ```NetworkX`` <https://networkx.github.io/documentation/stable/index.html>`__ for network analyses such as finding a least cost / shortest path between two points - install in *Anaconda Prompt* with \ ``conda install -c anaconda networkx``
-   ```owslib`` <http://geopython.github.io/OWSLib/>`__ to connect with *Open Geospatial Consortium* (*OGC*) web services - install in *Anaconda Prompt* with \ ``conda install -c conda-forge owslib``
-   ```postgresql`` <https://www.postgresqltutorial.com/postgresql-python/>`__ for SQL database connections -  install in *Anaconda Prompt* with \ ``conda install -c anaconda postgresql``
-   ```rasterio`` <https://rasterio.readthedocs.io/en/latest/>`__ for processing raster data as ```numpy`` <hypy_pynum.html#numpy>`__ arrays install in *Anaconda Prompt* with \ ``conda install -c conda-forge rasterio``
-   ```rasterstats`` <https://pythonhosted.org/rasterstats/>`__ produces zonal statistics of rasters and can interact with *GeoJSON* files - install in *Anaconda Prompt* with \ ``conda install -c conda-forge rasterstats``
-   ```sckit-image`` <https://scikit-image.org/>`__ for machine learning applied to georeferenced images - install in *Anaconda Prompt* with \ ``conda install -c anaconda scikit-image`` 