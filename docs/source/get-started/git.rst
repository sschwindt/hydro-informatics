About git
=========

*Git* is a fast, scalable, distributed revision control system, originally developed by *Linus Torvalds* (`read more about the git kernel <https://git.kernel.org/>`__). *Git* enables to coordinate work among collaborators beyond programming, in any set of files. Its support of non-linear workflows, speed and data integrity make git an indispensable tool in many industries and research. Before starting to read this *git* tutorial, have a look at the schematic functioning of repositories hosted with *git*.

.. figure:: ../img/git-scheme.png  
	
    The concept of git with some basic vocabulary.
	
The REMOTE frame is online (i.e., some one else’s computer) and the LOCAL frame is what happens on a personal computer, which is connected to the internet. Repositories can be newly created or forked remotely. Remote repositories can be cloned locally, modified locally, and local changes can be pushed to a remote repository. Collaborators want to make sure to regularly pull changes of a remote repository. Working with and on different branches becomes increasingly important with the number of developers and for the moment we just need to remember that we start working in the master branch (i.e., upstream origin / HEAD = master

.. _dl:

Install and use
---------------

The materials provided on these pages is best downloaded and updated using *git*-able environments (avoid downloading materials as *zip* file).

.. admonition:: Windows

   Download and install `Git Bash <https://git-scm.com/downloads>`__ and use it for example `PyCharm\ ’s Community Edition <https://www.jetbrains.com/pycharm/>`__.

.. admonition:: Linux

   You are already good to go: git is an integral feature of the most Linux distributions.

The repositories for this course are mainly hosted on *GitHub*. However, there are other *git* providers out there, such as `GitLab <https://gitlab.com/pages>`__, `plan.io <https://plan.io/knowledge-management/>`__, or `BitBucket <https://bitbucket.org/>`__.

Create
~~~~~~

To create a *git* repository, make sure to have access to a *git* provider. The most popular way to get access to a *git*-able server is to register with one of the long list of popular *git* providers.

.. tip::
   Students of the University of Stuttgart may use *GitHub* using their institutional ID (e.g., ``st9009133``) through the `TIK’s GitHub account and login page <https://github.tik.uni-stuttgart.de/login>`__.

Clone (download)
~~~~~~~~~~~~~~~~

*GitHub* provides detailed descriptions and standard procedures to work with their repositories (`read more <https://help.github.com/en/articles/cloning-a-repository>`__). The following “recipe guides through the first time download of *git* materials 

1. Open your favorite *git*-able command line:
  
	-   *Windows Option 1*: *PyCharm*      
	-   Go to the ``Terminal`` tab, which is usually at the bottom of    the window
	-   Go to the local target directory with the command |br|
 			 ``cd "D:/Target/Directory/"`` to change to the target installation directory. |br|
 			 If the directory does not exist, it can be created in the system explorer (right-click in empty space > ``New`` > ``Folder``).
	-   *Windows Option 2*: *Git Bash*   
	-   *Linux*: *Terminal* 
	
2. Clone the course repository (change materials according to the course attended):
   ``git clone https://github.com/hydro-informatics/materials]`` (or whatever repository you want to clone)

Done.

.. _update:

Update a local repository (re-pull)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*git* (within *Git Bash*, *PyCharm* or *Terminal*) is the only option to update local copies of a remote repository consistently. To do so, open one of the above mention *git*-able command lines and do the following:

1. Go to the local directory of the repository with the ```cd`` <https://en.wikipedia.org/wiki/Cd_(command )>`__ command (e.g., ``materials``): ``cd "D:/Python/materials/"`` (or wherever ``materials`` was cloned).
2. ``git status`` -  shows the modifications made.
3. Merge errors may occur when changes were made in the local copy. To avoid merge errors, type: ``git pull --rebase`` -  if locally edited scripts were modified remotely since the last pull, this will prompt issues and highlight problematic section with ``>>>``. Manually open concerned files and resolve the issues (delete invalid ``>>>`` highlights).
4. ``git push`` Done.

.. _push:

Update a remote repository (push local changes)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After editing files in a repository locally, *add* -  *commit* -  *push* (in that order) your edits to the remote copy of the repository with version control. To *add* - *commit* - *push* local changes to a remote repository, make sure to be the remote repository owner or a contributor. Then open a *git*-able terminal and type: 

1. ``git status`` -  this shows the modifications made. 
2. If the status seems OK with the consciously made changes, type ``git add .``; if only single files were changed, use ``git add filename.py`` instead. Best solution: use a local `.gitignore file <https://help.github.com/en/github/using-git/ignoring-files>`__. 
3. Commit changes ``git commit -m "Leave a message"`` - leave a significant and precise short message. 
4. ``git pull --rebase`` - if locally edited scripts were modified remotely since the last pull, this will prompt issues and highlight problematic section with ``>>>``. Manually open concerned files and resolve the issues (delete invalid ``>>>`` highlights). 
5. ``git push`` 

Done.

.. admonition:: Exercise

   Practice *git* with the `markdown & git <ex_git.html>`__ exercise.
