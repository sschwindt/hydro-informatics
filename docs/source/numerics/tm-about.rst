TELEMAC
=======

Two-dimensional (2d) numerical simulation methods described on these pages use the freely available software *open TELEMAC-MASCARET* (in the following referred to as *TELEMAC*), which was started as a commercial code by the R&D group of Électricité de France (EDF). Since 2010, the TELEMAC-MASCARET Consortium took over the development (EDF R&D is still deeply involved) and freely provides the software and its source code under a `GPLv3 license <http://www.gnu.org/licenses/gpl-3.0.html>`__. Visit their `website <http://www.opentelemac.org/>`__ to learn more about *TELEMAC*.

Get Started
-----------

It is strongly recommended to install `Debian Linux <https://www.debian.org/>`__ or one of its derivatives for working with *TELEMAC* (see the `Virtual Machines (VMs) <vm.html>`__ section in the *Software* chapter). Then, proceed with the installation of `TELEMAC <install-telemac.html>`__. Account for approximately 2 hours to get ready with *TELEMAC*.

General Introduction and Tutorial Guide
---------------------------------------

Analysis of a hydro-environment with *TELEMAC* involves pre-processing for abstracting the fluvial land scape, setting up control files, running a *TELEMAC* solver, and post-processing. The first-time user faces an overwhelming number of software options for pre- and post-processing. Besides, *TELEMAC* comes with a wide range of modules for 2d and 3d calculations of hydro-morphodynamic processes of various water bodies, from mountain rivers to coastal deltas under the influence of tides. Also, various sediment transport processes can be considered coupled with steady or unsteady flow conditions.

The tutorials on this website show how to:

-  Create a pure hydrodynamic model with steady-state runoff boundary conditions;
-  Implement unsteady boundary conditions (replace steady flow boundaries);
-  Activate modeling of sediment transport processes (morphodynamics) with *TELEMAC*\ ’s Gaia module.

Here, the focus is on modeling small to medium-sized rivers.

.. note::
   This page builds on descriptions provided in the `telemac2d <http://ot-svn-public:telemac1*@svn.opentelemac.org/svn/opentelemac/tags/v8p1r1/documentation/telemac2d/user/telemac2d_user_v8p1.pdf>`__ user manual.

Pre-processing
~~~~~~~~~~~~~~

Pre-processing involves abstracting the river land scape into a computational grid (mesh) with boundary conditions. Many software tools can be used for this purpose and this website features two options for mesh generation and defining geometry boundary conditions:

1. Use `QGIS <geo_software.html#QGIS>`__ and the `BASEmesh plugin <pre-QGIS.html#get-ready-with-QGIS>`__. The `QGIS Prepro option <pre-QGIS.html>`__ is convenient for creating geo-referenced 2d meshes and uses the pre-processing routines of `BASEMENT <basement.html>`__. So this is not an officially recommended version by the *TELEMAC* developers, but rather a home-brewed option on this website.
2. Use the National Research Council Canada’s `Blue KenueTM <install-telemac.html#bluekenue>`__ GUI software. The `Blue KenueTM Prepro option <telemac2d.html>`__ is preferably for *Windows* users and is somewhat cumbersome for creating geo-referenced point and line datasets to delineate the mesh.
3. Use `SALOME-HYDRO <install-telemac.html#SALOME>`__ for generating computational meshes in *MED* geometry files (more details in the `Telemac3d <telemac3d.html>`__ tutorial).

Model setup and run
~~~~~~~~~~~~~~~~~~~

The centerpiece of any *TELEMAC* model is the control (steering or *CAS*) file, which can be comfortably set up with `Fudaa PrePro <install-telemac.html#fudaa>`__. The basic setup of a `steady <telemac2d.html#steady>`__ and a `unsteady <telemac2d.html#unsteady>`__ model are explained on the `Model Setup page <telemac2d.html>`__. In addition, explanations are provided on the use of the `Gaia module for modeling morphodynamic (sediment transport) processes <telemac2d.html#prepro-gaia>`__.

Post-processing
~~~~~~~~~~~~~~~

*Artelia Eau et Environnement* created the `PostTelemac <https://plugins.QGIS.org/plugins/PostTelemac/>`__ plugin for *QGIS*, which is a powerful and convenient tool visualizing and post-processing *TELEMAC* simulation results. The `Telemac2d <telemac2d.html>`__ and `Telemac3d <telemac3d.html>`__ tutorials provide guidance on the usage of the *PostTelemac* plugin and `SALOME <install-openfoam.html#SALOME>`__ for post-processing *SLF* and *MED* results files, respectively.

The *TELEMAC* file structure
----------------------------

For any *TELEMAC* 2d simulation, the following input files are **mandatory**:

-  Steering file 
  
	-   File format: ``cas``   
	-   Prepare either with `Fudaa PrePro <telemac2d.html#prepro-fudaa>`__.

-  Geometry file 
  
	-   File format: ``.slf``    (`selafin <https://gdal.org/drivers/vector/selafin.html>`__) or ``.med`` (*MED* file library from the `SALOME-platform <https://www.SALOME-platform.org>`__)  
	-   Prepare either with `BlueKenueTM <install-telemac.html#bluekenue>`__ or `Fudaa PrePro <telemac2d.html#prepro-fudaa>`__.

-  Boundary conditions 
  
	-   File format: ``.cli`` (with ``slf``) or ``.bnd``/``.bcd`` (with ``.med``)	  
	-   Prepare ``.cli`` files with `BlueKenueTM <install-telemac.html#bluekenue>`__ and `Fudaa PrePro <telemac2d.html#prepro-fudaa>`__.
	-   Prepare ``.bnd``/``.bcd`` files either with *SALOME-HYDRO* or with a text editor (read more in the `Telemac3d tutorial <telemac3d.html#bnd-mod>`__)

There are many more file formats, which are not computationally mandatory for running a simulation with *TELEMAC*, but essential in practice to yield reasonable results with a hydro-morphodynamic model (i.e., coupled hydrodynamic-sediment transport solver). Such **optional** files are:

-  Liquid boundaries file (e.g., for water surface elevation or flow rates)
  
	-   Requires a stage-discharge relationship file   
	-   File format: ``.qsl`` 

-  Friction data file   
-  File format: ``tbl`` (``ASCII``)
-  Reference file to enable model validation (restart)
  
	-   File format: ``.slf`` or ``.med``   
	-   Check the *TELEMAC* docs 

-  Restart file for setting initial conditions (``.slf`` or ``.med``)
-  Sections file to set control sections (e.g., verify flow rates, velocity, or water surface elevation)
-  Sources (e.g., water or sediment) data file
-  Zones file   
-  Describes friction or other zonal properties 

When hydraulic structures are integrated into a model, some of the following files are required (depending on the structure type):

-  Culverts data file
-  Weirs data file 

In addition, a *FORTRAN* (``.f``) file can be created to specify special boundary conditions or the usage of either single or double precision 

.. tip::
   In hydro-morphodynamic modeling, single precision (i.e., 32-bit *floats*) rather than double precision (i.e., using 64-bit *floats*) is sufficient and much faster.

More input files can be defined to simulate oil spills, pollutant transport, wind, and tide effects.

--------------

Continue with setting up a mesh (*2dm* file) and a geometry file (*SLF*) with either 

-  `> QGIS > <pre-QGIS.html>`__, or
-  `> Blue KenueTM > <telemac2d.html>`__ 

--------------

Detailed file descriptions
--------------------------

The steering file (CAS)
~~~~~~~~~~~~~~~~~~~~~~~

The steering file is the main simulation file with information about mandatory files (e.g., the `selafin <https://gdal.org/drivers/vector/selafin.html>`__ geometry or the *cli* boundary), optional files, and simulation parameters. The steering file can be created or edited either with a basic text editor or advanced software such as `Fudaa-PrePro <install-telemac.html#fudaa>`__ or `BlueKenue <install-telemac.html#bluekenue>`__. In this example, we will use *BlueKenue*.

The geometry file (SLF or MED)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The geometry file in `slf (selafin or SERAFIN) <https://gdal.org/drivers/vector/selafin.html>`__ format contains binary data about the mesh with its nodes. The name format of the geometry file can be modified in the steering file with:

::

   /steering.cas GEOMETRY FILE   : 't2d_channel.slf'
   GEOMETRY FILE FORMAT  : SLF  / or MED with SALOME preferably for 3d 

*MED* files are typically processed with either `SALOME <install-openfoam.html#SALOME>`__ or `SALOME-HYDRO <install-telemac.html#SALOME-HYDRO>`__, which are featured in the `Telemac3d <telemac3d.html>`__ tutorial.

The boundary conditions (CLI or BND/BCD) and liquid boundary (QSL) files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The boundary file in *cli* format contains information about inflow and outflow nodes (coordinates and IDs). The *cli* file can be opened and modified with any text editor, which is not recommended to avoid inconsistencies. Preferably use `Fudaa-PrePro <install-telemac.html#fudaa>`__ or `BlueKenue <install-telemac.html#bluekenue>`__ for generating and /or modifying *cli* files.

In addition, users can define a liquid boundary conditions file (*qsl*) to define time-dependent boundary conditions (e.g., discharge, water depth, flow velocity or tracers).

The name format of the boundary conditions file can be modified in the steering file with:

::

   /steering.cas    
   BOUNDARY CONDITIONS FILE : 'bc_channel.cli'
   LIQUID BOUNDARIES FILE   : 'bc_unsteady.qsl'

Example (header only) for a boundary conditions file (*cli*):

::

     2 2 2  0.000  0.000  0.000  0.000 2  0.000  0.000  0.000    101     1
     2 2 2  0.000  0.000  0.000  0.000 2  0.000  0.000  0.000    102     2
     2 2 2  0.000  0.000  0.000  0.000 2  0.000  0.000  0.000    103     3
     ...

Example for a liquid boundary conditions file:

::

   # bc_unsteady.qsl    
   # Time-dependent inflow (discharge Q(2)) and outflow (depth SL(1))
   T           Q(1)     SL(2)
   s           m3/s     m    
   0.            0.     5.0
   500.        100.     5.0
   5000.       150.     5.0

The stage-discharge (or WSE-Q) file (txt - ASCII)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Define a stage-discharge file to use a stage (water surface elevation *WSE*)
-  discharge relationship for boundary conditions. Such files typically apply to the downstream boundary of a model at control sections (e.g., a free overflow weir). To use a stage-discharge file, define the following keyword in the steering file:

::

   /steering.cas    STAGE-DISCHARGE CURVES FILE : YEs 

Example for a stage-discharge file:

::

   # wse_Q.txt    
   # 
   Q(1)     Z(1)
   m3/s     m     
   50.     0.0
    60.     0.9
   100.     1.5

The friction data file (tbl - ASCII)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This optional file enables the definition of bottom friction regarding the roughness law to use and associated function coefficients. To activate and use friction data, define the following keywords in the steering file:

::

   /steering.cas    
   FRICTION DATA            : YES
   FRICTION DATA FILE       : 'friction.tbl' 

The results file (SLF or MED)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The name format of the results file can be modified in the steering file with:

::

   /steering.cas    
   RESULTS FILE             : 't2d_channel_output.slf'

Because this file is generated by *TELEMAC* when the simulation is running, it does not need to exist for starting the simulation. A good option for visualizing the results file is the `PostTelemac Plugin in QGIS <install-telemac.html#QGIS>`__: *MED* results files are typically processed with either `SALOME <install-openfoam.html#SALOME>`__ or `SALOME-HYDRO <install-telemac.html#SALOME-HYDRO>`__, which are featured in the `Telemac3d <telemac3d.html>`__ tutorial.
