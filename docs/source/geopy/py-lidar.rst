MARKDOWN FILE CONVERTED TO JUPYTEr
----------------------------------

Available at https://github.com/sschwindt/lidar-analysis 

.. tip::
   Use `QGIS <geo_software.html#QGIS>`__ to display geospatial data products.

Laspy 
-----

-  `Documentation <https://laspy.readthedocs.io/en/latest/>`__
-   `Tutorials <https://laspy.readthedocs.io/en/latest/tut_background.html>`__ 
Install
~~~~~~~

Type in *Anaconda Prompt*:

::

   conda install -c conda-forge laspy 

Find advanced installation instructions on `laspy.readthedocs.io <https://laspy.readthedocs.io/en/latest/tut_part_1.html>`__.

Usage
~~~~~

*laspy* uses *numpy* arrays to store data and this is why both libraries need be imported to read a *las* file:

.. code:: python 

   import numpy    import laspy    file_name = "/path/to/file/vanilla-valley.las"
   file_object = laspy.file.File("./path_to_file", mode="rw")

.. code:: python 

   import laspy 

   with laspy.file.File("./path_to_file", mode="rw") as las_file:
       pts = las_file.points 

   print(pts.dtype)
