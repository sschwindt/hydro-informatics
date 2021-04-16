Integrated Development Environments (IDEs)
==========================================

The teaching contents on this website build on so-called *Application Programming Inferace*\ s (*API*\ s) and *Integrated Development Environment*\ s (*IDE*\ s). An **API** represents a computing interface that enables interactions between multiple software intermediaries. Modular programming becomes easy with an *API*, because it systematically hides complex information that is not necessarily needed to write code according to industry standards. For instance, an *API* can define the interface between an application (such as *Python* or *Word*) and an *Operating System* (*OS*) such as *Windows*, *Linux*, or *macOS*. An **IDE** enables the definition of a project to use for example a specific `Python Conda Environment <https://docs.conda.io/>`__ and it enables robust coding by pointing out issues directly in the code, even before it was executed once. Powerful *IDE*\ s go even further and provide assistance in documenting code with markdown (*.md* files) and direct pipes into *git* (`see section on the usage of git <hy_git.html>`__).

.. note::
   These pages are written with the web-based *IDE* `JupyterLab <https://jupyter.org/>`__, which is suitable to follow the course contents. *IDE*\ s such as *PyCharm* or *Spyder* are more suitable to setup projects locally (e.g., for course assignments).

Anaconda 
--------

Anaconda Navigator
~~~~~~~~~~~~~~~~~~

*Anaconda* is basically a *Python* distribution that enables the usage of a couple of *IDE*\ s. Today, *Anaconda* is not limited to *Python* anymore and also comes with interfaces and environments for `R <https://www.r-project.org/about.html>`__.


.. note::
	`Anaconda <https://www.anaconda.com/distribution/>`__ represents the baseline for many applications presented on this website. It enables the built-in installation of programming language interpreters (e.g., *Python* and *R*), as well as *IDE*\ s such as `PyCharm <https://www.jetbrains.com/pycharm/>`__, `Spyder <https://www.spyder-ide.org/>`__, or `JupyterLab (Notebook) <https://jupyter.org/>`__.

The very first step to get started with *Anaconda* consists in downloading and installing `Anaconda <https://www.anaconda.com/distribution/>`__. On Windows, *Anaconda* (`download <https://docs.anaconda.com/anaconda/install/windows/>`__) should be installed in the *LOCAL* user folder (e.g., \*C::raw-latex:`\users`<your-user-name>:raw-latex:`\AppData`:raw-latex:`\Local*`). Linux or macOS users find download and installation instructions directly at the developer’s website, tailored for their specific distribution. `Click here for Linux installation instructions <https://docs.anaconda.com/anaconda/install/linux/>`__ and `click here for macOS installation instructions <https://docs.anaconda.com/anaconda/install/mac-os/>`__.

After the successful installation of *Anaconda*, *IDE*\ s for *Python* programming or *markdown* editing can be directly installed by launching the **Anaconda navigator**. **``conda``** environments can be created later on following the `instructions in the Python (fundamentals) section <hypy_install.html#conda-env>`__.

Miniconda
~~~~~~~~~

*Anaconda* may create large environments that require several gigabytes of storage. To install lightweight environments, use `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`__. *Miniconda* does not include *Anaconda Navigator* and to enable working with *Jupyter* notebooks (in *Windows*):

1. Click on *Start*.
2. Type ``Anaconda Prompt`` and hit enter (use *Miniconda3*). A *Terminal* window (black background) opens.
3. In *Anaconda prompt* type ``conda install jupyter`` and confirm with ``y`` when the *Terminal* asks ``Proceed ([y]/n)?``.

To work with *Jupyter* notebooks (open, create or modify), type ``jupyter lab`` (or ``jupyter notebook``) in *Anaconda Prompt (Miniconda3)* and hit *Enter*. The *JupyterLab* application will open in the default webbrowser.

.. _pycharm:

PyCharm (via Anaconda Navigator)
--------------------------------

*Jetbrains* `PyCharm (Community Edition) <https://www.jetbrains.com/pycharm/>`__ is an open-access IDe for non-commercial use. Alternatives are `Spyder IDE <https://www.spyder-ide.org/>`__ (for *Python*) or `RStudio <https://rstudio.com/>`__ (*R* and *Python*). However, before launching any project in an *IDE*, the installation of an interpreter (e.g., *Python* or *R*) is necessary (we already installed an interpreter with *Anaconda*).

*PyCharm* is available as an *Anaconda Navigator* (i.e., *Anaconda*\ ’s graphical user interface) module. To enable *PyCharm* in *Anaconda*, download *PyCharm* from the `developer’s website <https://www.jetbrains.com/pycharm/promo/anaconda/>`__ and install *PyCharm*. A reboot may be required after the installation.

After the installation of *PyCharm* for *Anaconda*, open *Anaconda Navigator*:

1. Open *Anaconda Navigator* and make sure to be in the *Home* tab.
2. If the installation of *PyCharm* was successful, click on the    *Launch* button to open *PyCharm*.
3. In *PyCharm* click on ``+ Create New Project`` 
4. Option 1 (preferred): Use the `developer’s up-to-date documentation <https://docs.anaconda.com/anaconda/user-guide/tasks/pycharm/>`__ for setting up *PyCharm* with *Anaconda*.
5. Option 2 (quick to read, but may fail): A window will open - enter:
  
	-   *Location* 	-  Select a local directory for the project (e.g., *C:/hydro/project*)	  
	-   *Project Interpreter* -  Check the ``Existing interpreter`` box and select the above-installed `conda environment ``hypy`` <hypy_install.html#conda-env>`__ (e.g., ``C:\users\<your-user-name>\AppData\Local\Continuum\anaonda3\envs\``)
	-   Click on the ``Create`` button.

All set - you are ready to work with *Python*, markdown (documentation), and `git <hy_git.html>`__.

.. note::
   **Python users** read more about setting up *conda* environments on the `Python (basics) <hypy_install.html#ide-setup>`__ page.

.. _jupyter:

JupyterLab
----------

Via Anaconda Navigator
~~~~~~~~~~~~~~~~~~~~~~

*JupyterLab* is a product of the nonprofit organization `Project Jupyter <https://jupyter.org/>`__, which develops “open-source software, open-standards, and services for interactive computing across dozens of programming languages. A *Jupyter* notebook (*.ipynb* file) enables the combination of markdown text blocks with executable code blocks. Essentially, a *Jupyter* notebook is a *JavaScript Object Notation* (`JSON <https://www.json.org/json-en.html>`__) file. The structure of *JSON* files enables the easy export of *.ipynb* notebooks to many other open standard output formats such as *HTML*, `LaTeX <https://latex-project.org/>`__, *markdown*, *Python*, *presentation slides*, or *PDF*. The *Jupyter* kernels support the three core programming languages **Ju**\ lia, **Pyt**\ hon and **R**, and many more *Jupyter* kernels (currently 49) for other programming languages exist.

1. Open *Anaconda Navigator* and make sure to be in the *Home* tab.
2. Look for *JupyterLab* and click on the *Install* button (if already installed, there is only a *Launch* button visible).
3. After successful installation, open *JupyterLab*, by clicking on the *Launch* button.
4. *JupyterLab* opens in the default web browser, where *Jupyter* notebooks (*.ipynb*) or *Python* files can be created and edited.

.. tip::
   Get familiar with *JupyterLab*, by creating files, adding new *Markdown* or *Python* cells and ``Run``\ ning cells.
   
The essentials of *markdown* are explained on the `Markdown and Documentation <hy_documentation.html#markdown>`__ page (short read). Learning *Python* is more than a short read and the `Python (basics) <python.html>`__ walks you through the course contents to learn *Python* (takes time).

.. note::
   *Anaconda Navigator* alternatively provides the application *Jupyter Notebook*. However, *JupyterLab* is the *Project Jupyter*\ ’s next-generation user interface, which is more flexible and powerful. This is why this website refers to *JupyterLab* rather than the *Jupyter Notebook* app.

Via *Anaconda Prompt* 
~~~~~~~~~~~~~~~~~~~~~

Open *Anaconda Prompt*, which represents a *Terminal* window with black background and a blinking cursor.

If you are working with *Miniconda*, install the *Jupyter Notebook* app by typing ``conda install jupyter`` and confirm with ``y`` when *Anaconda Prompt* asks ``Proceed ([y]/n)?``.

To start the *JupyterLab* app and open, create, or modify *Jupyter* notebooks, type ``jupyter lab`` (``jupyter notebook`` for *Jupyter Notebook*) in *Anaconda Prompt (Miniconda3)* and hit *Enter*. The *Jupyter Notebook* application will open in the default webbrowser.

Extensions and spellchecker
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Many additional features for *JupyterLab* are available through `nbextensions <https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html>`__, which can be installed through *Anaconda Prompt*:

::

   conda install -c conda-forge jupyter_contrib_nbextensions 

When reading through the *Python* tutorials on this website, you will probably find one or another spelling mistake (please report mistakes!). In particular, the *Python* pages are affected, because they were created with *Jupyter Lab*, where there is no spell checker pre-installed. To avoid at least the most unpleasant errors you can install a spellchecker in *jupyter*. One solution is to install `@ijmbbarr <https://github.com/ijmbarr/jupyterlab_spellchecker>`__\ s spellchecker, which requires installing *nodejs* (through *Anaconda Prompt* and in addition to *nbextensions*):

::

   conda install -c conda-forge nodejs    
   jupyter labextension install @ijmbarr/jupyterlab_spellchecker 

The spellchecker uses `Typo.js <https://github.com/cfinke/Typo.js>`__ as dictionary and only identifies misspelled words without proposing corrections. More details on spellchecking are available at the `developer’s website <https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/nbextensions/spellchecker/README.html>`__.

In the case that several warning messages occur when starting *JupyterLab* (such as ``[W 18:49:22.283 NotebookApp] Config option template_path not recognized by LenvsHTMLExporter. Did you mean one of: template_file, template_name, template_paths?``), downgrade *jupyter notebook* from version 6.x to 5.6.1 (there is currently an issue with the ``temp_path`` variable):

::

   conda install "nbconvert=5.6.1"
