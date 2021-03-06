Packages and Modules (Libraries)
================================

Summary: Import external libraries and organize your code into
functional chunks.

The *html* version of this notebook is hosted at
https://hydro-informatics.github.io/hypy_pckg.html.

Import packages or modules
--------------------------

Importing a package or module in *Python* makes external functions and
other elements (such as objects) of modules accessible in a script. The
functions and other elements are stored within another *Python* file
(``.py``) in some */site_packages/* folder of the interpreter
environments. Thus, in order to use a non-standard package, it needs to
be downloaded and installed first. Standard packages (e.g., ``os``,
``math``) are always accessible and other can be added with *conda*
(`read the installation
instructions <https://hydro-informatics.github.io/hypy_install.html#install-pckg>`__).

   **Note**: There is a **difference between modules and packages**.
   Modules are single or multiple files that can be imported as one
   import (e.g., ``import a_module``). Packages are a collection of
   modules in a directory with a defined package hierarchy, which
   enables the import of individual modules
   (e.g. ``from a_package.module import a_function``). Packages are
   therefore also modules, but with a hierarchy definition (i.e., a
   ``__path__`` attribute and a ``__init__.py`` file). Sounds fuzzy?
   Read this page down to the bottom and come back here to re-read this
   note.

The ``os`` package provides some useful system-terminal like commands,
for example, to manage folder directories. So let’s import this
essential package.

.. code:: ipython3

    import os
    print(os.getcwd()) # print current working directory
    print(os.path.abspath('')) # print directory of script running


.. parsed-literal::

    C:\Users\schwindt\jupyter\nb-lectures
    C:\Users\schwindt\jupyter\nb-lectures
    

Overview of import options
~~~~~~~~~~~~~~~~~~~~~~~~~~

Here is an overview of options to import packages or modules
(hierarchical parts of packages):

+--------------+--------------------+----------------------------------+
| Command      | Description        | Usage of attributes              |
+==============+====================+==================================+
| ``import pa  | Import an original | ``package.item()``               |
| ckage-name`` | module             |                                  |
+--------------+--------------------+----------------------------------+
| ``import pac | Import module and  | ``nick-name.item()``             |
| kage-name as | rename (alias) it  |                                  |
|  nick-name`` | in the script      |                                  |
+--------------+--------------------+----------------------------------+
| ``from pa    | Import only a      | ``item()``                       |
| ckage-name i | function, class or |                                  |
| mport item`` | other items        |                                  |
+--------------+--------------------+----------------------------------+
| ``from       | Import all items   | ``item()``                       |
|  package-nam |                    |                                  |
| e import *`` |                    |                                  |
+--------------+--------------------+----------------------------------+

Example
~~~~~~~

.. code:: ipython3

    import matplotlib.pyplot as plt # import pyplot from the matplotlib module and alias it with plt
    import math as m
    
    x = []
    y = []
    
    for e in range(1, 10):
        x.append(e)
        y.append(e**2)
    
    plt.plot(x, y)




.. parsed-literal::

    [<matplotlib.lines.Line2D at 0x15f7594b388>]



What is the best way to import a package or module?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There is no global answer to this questions. However, be aware that
``from package-name import *`` overwrites any existing variable or other
item in the script. Thus, only use ``*`` when you are aware of all
contents of a module.

.. code:: ipython3

    pi = 9.112 # define a float called pi 
    print("Pi is not %1.3f." % pi)
    
    from math import pi # this overwrites the before defined variable pi
    print("Pi is %1.3f." % pi)


.. parsed-literal::

    Pi is not 9.112.
    Pi is 3.142.
    

   **Tip**: Define default import packages for *JupyterLab*\ ’s
   *IPython* kernel (read more on the `Python installation
   page <https://hydro-informatics.github.io/hypy_install.html#ipython>`__).

What items (attributes, classes, functions) are in a module?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sometimes we want to explore modules or to check variable attributes.
This is achieved with the ``dir()`` command:

.. code:: ipython3

    import sys
    print(sys.path)
    print(dir(sys.path))
    
    a_string = "zabaglione"
    print(", ".join(dir(a_string)))


.. parsed-literal::

    ['C:\\Users\\schwindt\\jupyter\\nb-lectures', 'C:\\Users\\schwindt\\Anaconda3\\python37.zip', 'C:\\Users\\schwindt\\Anaconda3\\DLLs', 'C:\\Users\\schwindt\\Anaconda3\\lib', 'C:\\Users\\schwindt\\Anaconda3', '', 'C:\\Users\\schwindt\\AppData\\Roaming\\Python\\Python37\\site-packages', 'C:\\Users\\schwindt\\Anaconda3\\lib\\site-packages', 'C:\\Users\\schwindt\\Anaconda3\\lib\\site-packages\\win32', 'C:\\Users\\schwindt\\Anaconda3\\lib\\site-packages\\win32\\lib', 'C:\\Users\\schwindt\\Anaconda3\\lib\\site-packages\\Pythonwin', 'C:\\Users\\schwindt\\Anaconda3\\lib\\site-packages\\IPython\\extensions', 'C:\\Users\\schwindt\\.ipython']
    ['__add__', '__class__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__iadd__', '__imul__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__rmul__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'append', 'clear', 'copy', 'count', 'extend', 'index', 'insert', 'pop', 'remove', 'reverse', 'sort']
    __add__, __class__, __contains__, __delattr__, __dir__, __doc__, __eq__, __format__, __ge__, __getattribute__, __getitem__, __getnewargs__, __gt__, __hash__, __init__, __init_subclass__, __iter__, __le__, __len__, __lt__, __mod__, __mul__, __ne__, __new__, __reduce__, __reduce_ex__, __repr__, __rmod__, __rmul__, __setattr__, __sizeof__, __str__, __subclasshook__, capitalize, casefold, center, count, encode, endswith, expandtabs, find, format, format_map, index, isalnum, isalpha, isascii, isdecimal, isdigit, isidentifier, islower, isnumeric, isprintable, isspace, istitle, isupper, join, ljust, lower, lstrip, maketrans, partition, replace, rfind, rindex, rjust, rpartition, rsplit, rstrip, split, splitlines, startswith, strip, swapcase, title, translate, upper, zfill
    

Create a module
---------------

In object-oriented programming and code factorization, writing own, new
modules is an essential task. In order to write a new module, first
create a new script. Then, open the new script and add some parameters
and functions.

.. code:: ipython3

    # icecreamdialogue.py
    flavors = ["vanilla", "chocolate", "bread"]
    price_scoops = {1: "two euros", 2: "three euros", 3: "your health"}
    welcome_msg = "Hi, I only have " + flavors[0] + ". How many scoops do you want?"

```icecreamdialogue.py`` <https://github.com/hydro-informatics/icecream/raw/master/single-scripts/icecreamdialogue.py>`__
can now either be executed as script (nothing will happen visibly) or
imported as module to access its variables (e.g.,
``icecreamdialogue.flavors``).

.. code:: ipython3

    import icecreamdialogue as icd
    print(icd.welcome_msg)
    scoops_wanted = 2
    print("That makes {0} please".format(icd.price_scoops[scoops_wanted]))


.. parsed-literal::

    Hi, I only have vanilla. How many scoops do you want?
    That makes three euros please
    

Make a script stand-alone
~~~~~~~~~~~~~~~~~~~~~~~~~

As an alternative, we can append the call to items in
```icecreamdialogue.py`` <https://github.com/hydro-informatics/icecream/raw/master/single-scripts/icecreamdialogue.py>`__
in the script and run it as a stand-alone script by adding the called
item in to a ``if (__name__ == '__main__'):`` statement:

.. code:: ipython3

    # icecreamdialogue_standalone.py
    flavors = ["vanilla", "chocolate", "bread"]
    price_scoops = {1: "two euros", 2: "three euros", 3: "your health"}
    welcome_msg = "Hi, I only have " + flavors[0] + ". How many scoops do you want?"
    
    
    if (__name__ == '__main__'):
        print(welcome_msg)
        scoops_wanted = 2
        print("That makes {0} please".format(price_scoops[scoops_wanted]))


.. parsed-literal::

    Hi, I only have vanilla. How many scoops do you want?
    That makes three euros please
    

Now we can run
```icecreamdialogue_standalone.py`` <https://github.com/hydro-informatics/icecream/raw/master/single-scripts/icecreamdialogue_standalone.py>`__
in the terminal (e.g., *PyCharm*\ ’s *Terminal* tab at the bottom of the
window).

::

   C:\temp\ python icecreamdialogue_standalone.py

   **Note**: Depending on the definition of system variables used in the
   *Terminal* environment, the *Python* must be called with a different
   variable name then ``python`` (e.g., ``python3`` on many *Linux*
   platforms).

Make standalone script with input parameter
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To make the script more flexible, we can define ``scoops_wanted`` as an
input variable of a function.

.. code:: python

   # icecreamdialogue_standalone_withinput.py
   flavors = ["vanilla", "chocolate", "bread"]
   price_scoops = {1: "two euros", 2: "three euros", 3: "your health"}
   welcome_msg = "Hi, I only have " + flavors[0] + ". How many scoops do you want?"

   def dialogue(scoops_wanted): #formerly in the __main__ statement
       print(welcome_msg)
       print("That makes {0} please".format(price_scoops[scoops_wanted]))

   if (__name__ == '__main__'):
       # import the terminal function emulator sys
       import sys
       if len(sys.argv) > 1: # make sure input is provided
           # if true: call the dialogue function with the input argument
           dialogue(int(sys.argv[1]))

Now we can run ``icecreamdialogue_standalone_withinput.py`` in the
terminal.

::

   C:\temp\ python3 icecreamdialogue_standalone.py 2

Initialization of a package (hierarchically organized module)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Good practice involves that one script does not exceed 50-100 lines of
code. In consequence, a package will most likely consist of multiple
scripts that are stored in one folder and one master script serves for
the initiation of the scripts. This master script is called
``__init__.py`` and *Python* will always invoke this script name in a
package folder. Example structure of a module called ``icecreamery``:

-  ``icecreamery`` (folder name)

   -  ``__init__.py`` - package initiation *Python* script
   -  ``icecreamdialogue.py`` - dialogue producing *Python* script
   -  ``icecream_maker.py`` - virtual ice cream producing *Python*
      script

In order to automatically invoke the two relevant scripts (sub-modules)
of the ``icecreamery`` module, the ``__init__.py`` needs to include the
following:

.. code:: ipython3

    # __init__.py
    print(f'Invoking __init__.py for {__name__}') # not absolutely needed ..
    import icecreamery.icecreamdialogue, icecreamery.icecream_maker


.. parsed-literal::

    Invoking __init__.py for __main__
    Invoking __init__.py for icecreamery
    

.. code:: ipython3

    # example usage of the icecreamery package
    import icecreamery
    print(icecreamery.icecreamdialogue.welcome_msg)


.. parsed-literal::

    Hi, I only have vanilla. How many scoops do you want?
    

Do you remember the ``dir()`` function? It is intended to list all
modules in a package, but it does not do so unless we defined an
``__all__`` list in the ``__init__.py``.

.. code:: python

   # __init__.py with __all__ list
   __all__ = ['icecreamdialogue', 'icecream_maker']

The full example of the ``icecreamery_all`` package is available in the
`icecream <https://github.com/hydro-informatics/icecream>`__ repository.

.. code:: ipython3

    # example usage of the icecreamery package
    from icecreamery_all import *
    print(icecreamdialogue.welcome_msg)


.. parsed-literal::

    Hi, I only have vanilla. How many scoops do you want?
    

Package creation summary
~~~~~~~~~~~~~~~~~~~~~~~~

A hierachically organized package contains a ``__init__.py`` file with
an ``__all__`` list to invoke relevant module scripts. The structure of
a module can be more complex than the above example list (e.g., with
sub-folders). When you write a package, remember to use `meaningful
script and variable
names <https://hydro-informatics.github.io/hypy_pystyle.html#libs>`__,
and to document it.

   **Tip**: Implement a custom
   `logger <https://hydro-informatics.github.io/hypy_pyerror.html#logging>`__
   in your module with ``logger = logging.getLogger(__name__)`` (replace
   ``__name__`` with for example ``my-module-log``).

Reload (re-import) a package or module
--------------------------------------

Since *Python3* reloading a module requires to import the ``importlib``
module first. Reloading makes only sense if you are actively writing a
new module. To reload any module type:

.. code:: python

   import importlib
   importlib.reload(my-module)

