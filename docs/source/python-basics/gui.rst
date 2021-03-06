Graphical User Interfaces
=========================

.. image:: ../../img/hello-gui.png

A Graphical User Interface (GUI) facilitates setting input variables of
scripts. This is particularly useful if you want to reuse a script that
you have written a long time ago without having to study the whole
script again in detail. Although it is arguable whether GUIs are still
appropriate in times of web applications, large and  in particular
copyrighted data must be processed locally. and  for local data
processing, a GUI is a very convenient way to control self-written,
custom programs.

Several GUI library (packages) are available for *Python* and  this introduction uses the ```tkinter`` <https://docs.python.org/3/library/tkinter.html>`__ library. Alternatives are, for example, `wxPython <https://www.wxpython.org/>`__ or `Jython <https://www.jython.org/>`__ (a *Java* implementation of *Python 2*). ``tkinter`` is a stand ard library, which does not need to be installed additionally. For a quick example, type in the terminal (e.g., *PyCharm* or *Linux* terminal - not in the *Python* console):

::

   python -m tkinter

.. admonition:: Linux

   If you encounter troubles with ``tkinter`` on *Linux*, make sure that ``tkinter`` for *Python* is installed, either with \ ``sudo apt-get install python3-tk`` or \ ``sudo apt-get install python3.X-tk`` (replace ``X`` with your *Python* version) or ``sudo apt install tk8.6-dev`` to install the library only (this should be sufficient). If the above comments do not work, make sure that the ``tkinter`` repository is available to your system: ``sudo add-apt-repository ppa:deadsnakes/ppa`` (the repository address may change and  depends on your *Linux* and  *Python* versions).

``tkinter`` works on many popular platforms (*Linux*, *macOS*,
*Windows*) and  is not only available to *Python*, but also to
`Ruby <https://www.ruby-lang.org>`__, `Perl <https://www.perl.org/>`__,
`Tcl <https://www.tcl-lang.org/>`__ (the origin of of ``tkinter``), and 
many more languages. Because of its support for languages like *Ruby* or
*Perl*, ``tkinter`` can be used for local GUIs as well as for web
applications.

.. note::
   All GUI codes on this pages can be downloaded from the `course repository <https://github.com/hydro-informatics/material-py-codes/raw/master/gui/>`__.

The first GUI
-------------

The very first step is to import ``tkinter``, usually using the alias
``as tk``. With ``tk.Tk()``, a so-called parent window (e.g., ``top``)
can be created, in which all further elements will be accommodated. All
further elements are created as ``tk`` objects as child of the parent
window and  placed (arranged) in the parent window using the ``pack()``
or the ``grid()`` (e.g., ``tk.ELEMENT.grid(row=INT, column=INT)``)
methods (more later in the `widgets <#place-widget>`__ section).

To display the GUI, the parent window ``top`` must be launched with
``top.mainloop()`` after arranging all elements. The following code
block shows how to create a parent window with a label element
(``tk.Label``).

.. code:: python

   import tkinter as tk
   top = tk.Tk()
   a_label = tk.Label(top, text = "A label just shows some text.")
   a_label.pack()
   top.mainloop()

.. image:: ../../img/py-tk-first.png


After calling the ``mainloop()`` method, a window opens in a *wait*
state. That means, the window is waiting for ``events`` being triggered
through user action (e.g., a click on a button). This is called
*event-driven programming*, where *event hand lers* are called rather
than a single linear flow of (*Python*) command s.

For now, our window uses default values, for example, defaults for the
window title, size and  background color. These window properties can be
modified with the ``title``, ``minsize`` or ``maxsize``, and 
``configure`` attributes of the ``top`` parent window:

.. code:: python

   top = tk.Tk()
   a_label = tk.Label(top, text="A label just shows some text.")
   a_label.pack()

   top.title("My first GUI App")
   top.minsize(628, 382)
   top.configure(bg="sky blue")
   top.mainloop()

.. image:: ../../img/py-tk-first-config.png  

Add a Button to call a function
-------------------------------

So far our window only shows a (boring) label, while it is waiting for
events that are not defined (no functions, no buttons). With a
``tk.Button``, we can add an event trigger. In addition, we will define
a ``call_back`` function that creates an *infobox*, which represents a
trigger-able event. Note that an *infobox* is a ``showinfo`` object
imported from ``tkinter.messagebox``.

.. code:: python

   from tkinter.messagebox import showinfo
   # more message boxes: askokcancel, askyesno

   def call_back(message):
       showinfo("This is an Infobox", message)


   top = tk.Tk()
   a_label = tk.Label(top, text="Here is the button.")
   a_label.pack()
   # add a button
   a_button = tk.Button(top, text = ">> Click <<", command =lambda: call_back("Greetings from the Button."))
   a_button.pack()
   top.mainloop()

.. image:: ../../img/py-tk-button.png


.. note::
   The ``command `` receives a??```lambda`` <hypy_pyfun.html#lambda>`__ function that links to the ``call_back`` function. Why do we need this complication? The answer is that the ``call_back`` function would be automatically  triggered with the ``mainloop()`` method if we were not using a ``lambda`` function here.

A vanilla ``tkinter`` program
-----------------------------

In the above sections, we have created single ``tkinter`` objects (*widgets*) in a straightforward script-style. However, when we write a GUI, we most likely want to start an application (*App*) by just running a script. This is why ``tkinter`` widgets are usually created as objects of customized classes. Therefore, we want to recast our example as object-oriented code according to the template from the `lecture on Python classes <hypy_classes.html#template>`__.

The next code block creates a ``VanillaApp``, which is a child of
``tk.Frame`` (``tkinter`` parent frame). Thus, the initialization method
(``__init__``) needs to invoke ``tk.Frame`` and  ``pack()`` itself to
initialize the window. After that, we can place other ``widget``\ s such
as labels and  buttons as before. In the ``VanillaApp``, we can also
directly implement the ``call_back`` function as a method. Moreover, we
want the below script to run stand -alone, also it is not part of a
beautiful *jupyter* notebook. For this reason, the
``if __name__ == "__main__": VanillaApp().mainloop()`` statement is
required at the bottom of the script (read more about the ``__main__``
statement on the `packages page <hypy_pckg.html#stand alone>`__).

.. code:: python

   # define the VanillaApp class
   class VanillaApp(tk.Frame):
       def __init__(self, master=None):
           tk.Frame.__init__(self, master)
           self.pack()
           
           table_label = tk.Label(master, text="Do you want vanilla ice?")
           table_label.pack()
           vanilla_button = tk.Button(master, text = "I want Vanilla", command =lambda: call_back("Here is Vanilla!"))
           vanilla_button.pack()
           no_vanilla_button = tk.Button(master, text = "I want something else", command =lambda: call_back("Here is bread!"))
           no_vanilla_button.pack()
           
       def call_back(self, message):
           showinfo("This is an Infobox", message)


   # instantiate a VanillaApp object
   if __name__ == "__main__":
       VanillaApp().mainloop()

.. image:: ../../img/py-tk-vanilla.png 

.. tip::
   The above code block with the ``VanillaApp`` class can be copied to any external *Python* file and saved as, for example, ``vanilla_app.py``. With *Python* being defined as a `system variable  <https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables>`__ (only necessary in *Windows* - point at your *Anaconda* base environment???s *Python* executable), the GUI can be started as follows:
   
   1. Open Terminal (or a *Command  prompt* ``cmd`` in *Windows*).
   2. Navigate to the directory where the script is located (use ``cd`` in `Windows <https://docs.microsoft.com/en-us/windows-server/administration/windows-command s/cd>`__ or `Linux/macOS <http://www.linfo.org/cd.html>`__).
   3. Type ``python vanilla_app.py`` (or ``python -m vanilla_app.py``) to launch the GUI.Another tip: this sequence of command s can also be written to a batch file (```.bat`` on Windows <https://www.wikihow.com/Write-a-Batch-File>`__) or shell script (`.sh on Linux/macOS <https://www.linux.com/training-tutorials/writing-simple-bash-script/>`__ - `alternative source <http://linuxcommand .org/lc3_writing_shell_scripts.php>`__).
   
   Then, a double click on the batch file starts the *Python*-based GUI.


More *Widget*\ s
----------------

*Tkinter* provides many more widgets than just labels and  buttons. The
following illustration features some widgets with a:

-  definition of a GUI window name with ``master.title("Window name")``
-  definition of a GUI window icon (ICO) with
   ``master.iconbitmap("directory/icon_file.ico")``
-  ``tk.Menu`` with drop down cascade
-  ``tk.Label`` (see above)
-  ``tk.Button`` (see above)
-  ``tk.Entry`` - a blank field where users can enter values or words
-  ``ttk.Combobox`` - a drop down menu in the parent frame
   (`tk-themed <https://docs.python.org/3/library/tkinter.ttk.html>`__
   ``ttk`` widget)
-  ``tk.Listbox`` with a ``tk.Scrollbar``, where the scrollbar is
   required to navigate to *listbox* entries that are not in the visible
   range of the *listbox* size
-  ``tk.Checkbutton`` that can be checked (ticked) to set a
   ``tk.BooleanVar()`` object to ``True`` (default: not checked ->
   ``False``)Alternatively, have a look at
   ```tk.Radiobutton`` <http://effbot.org/tkinterbook/radiobutton.htm>`__
   to enable selections from a multiple-choice frame (rather than the
   ``False``-``True``-only frame of a *checkbutton*)
-  ``tk.PhotoImage`` to display a sub-sampled image in the GUI

.. figure:: ../../img/py-tk-elements.png
	
   tkinter widgets: Label, Button, Entry, Combobox, Listbox with Scrollbar, Checkbutton, and an Image.

This is the code that creates the ``tkinter`` widgets in the above figure (the `script <https://github.com/hydro-informatics/material-py-codes/raw/master/gui/start_gui.py>`__, `image <https://github.com/hydro-informatics/material-py-codes/raw/master/gui/sunny_image.gif>`__ and  `icon <https://github.com/hydro-informatics/material-py-codes/raw/master/gui/sample_icon.ico>`__ are available at the course repository):

.. code:: python

   import tkinter as tk
   from tkinter.messagebox import showinfo
   from tkinter import ttk


   class MyApp(tk.Frame):
       def __init__(self, master=None):
           tk.Frame.__init__(self, master)

           self.master.title("Master Title")
           self.master.iconbitmap("gui/sample_icon.ico")

           # Set geometry: upper-left corner of the window
           ww = 628  # width
           wh = 382  # height
           wx = (self.master.winfo_screenwidth() - ww) / 2
           wy = (self.master.winfo_screenheight() - wh) / 2
           # assign geometry
           self.master.geometry("%dx%d+%d+%d" % (ww, wh, wx, wy))
           # assign space holders around widgets
           self.dx = 5
           self.dy = 5

           # Menu Bar
           self.mbar = tk.Menu(self)  # create stand ard menu bar
           self.master.config(menu=self.mbar)  # make self.mbar stand ard menu bar
           # add menu entry
           self.ddmenu = tk.Menu(self, tearoff=0)
           self.mbar.add_cascade(label="A Drop Down Menu", menu=self.ddmenu)  # attach entry it to stand ard menu bar
           self.ddmenu.add_command (label="Drop Down Entry 1", command =lambda: self.hello("Drop Down Menu!"))

           # Label
           self.a_label = tk.Label(master, text="A Label")
           self.a_label.grid(column=0, row=0, padx=self.dx, pady=self.dy)

           # Button
           self.a_button = tk.Button(master, text="A Button", command =lambda: self.hello("The Button!"))
           self.a_button.grid(column=0, row=1, padx=self.dx, pady=self.dy)

           # Entry
           self.an_entry = tk.Entry(master, width=20)
           self.an_entry.grid(column=0, row=2, padx=self.dx, pady=self.dy)

           # Combobox
           self.cbox = ttk.Combobox(master, width=20)
           self.cbox.grid(column=0, row=3, padx=self.dx, pady=self.dy)
           self.cbox['state'] = 'readonly'
           self.cbox['values'] = ["Combobox Entry 1", "Combobox Entry 2", "Combobox Entry ..."]
           self.cbox.set("Combobox Entry 1")
           self.cbox_selection = self.cbox.get()

           # Listbox with Scrollbar
           self.scrlbar = tk.Scrollbar(master, orient=tk.VERTICAL)
           self.scrlbar.grid(stick=tk.W, column=1, row=4, padx=self.dx, pady=self.dy)
           self.lbox = tk.Listbox(master, height=3, width=20, yscrollcommand =self.scrlbar.set)
           for e in ["Listbox Entry 1", "Listbox Entry 2", "With Scrollbar ->", "lb entry n"]:
               self.lbox.insert(tk.END, e)
           self.lbox.grid(sticky=tk.E, column=0, row=4, padx=self.dx, pady=self.dy)
           self.scrlbar.config(command =self.lbox.yview)
           self.lbox_selection = self.lbox.get(0)

           # Checkbutton
           self.check_variable = tk.BooleanVar()
           self.cbutton = tk.Checkbutton(master, text="Tick this Checkbutton", variable=self.check_variable)
           self.cbutton.grid(sticky=tk.E, column=2, row=0, padx=self.dx, pady=self.dy)

           # Image
           logo = tk.PhotoImage(file="gui\\sunny_image.gif")
           logo = logo.subsample(2, 2)  # controls size
           self.l_img = tk.Label(master, image=logo)
           self.l_img.image = logo
           self.l_img.grid(row=1, column=2, rowspan=4)
           # create a placeholder to relax layout
           tk.Label(text="                                                    ").grid(row=0, column=1)
           
       @staticmethod
       def hello(message):
           showinfo("Got Message from ...", message)


   if __name__ == '__main__':
       MyApp().mainloop()

As usual in *Python*, there are many more options (widgets) available.
`effbot.org <http://effbot.org/tkinterbook/>`__ offers a detailed
overview of available ``tkinter`` objects.

``tkinter`` variables
---------------------

In the above example, the checkbox receives a ``tk.BooleanVar()``, which
takes a ``True`` value when a user checks the checkbox. There are more
variables that can be associated with a ``tkinter`` widget (e.g., an
``tk.Entry``, a ``tk.Listbox``, or a ``ttk.Combobox``). ``tkinter``
variables correspond basically to `Python data
types <hypy_pybase.html#var>`__ with special methods that are required
to set or retrieve (get) user-defined values of these data types. Here
is an overview on some ``tkinter`` variables:

-  ``tk.BooleanVar()`` of type *boolean* can be ``True`` or ``False``
-  ``tk.DoubleVar()`` is a numeric floating point (*float*) variable
-  ``tk.IntVar()`` is a numeric *integer* variable
-  ``tk.StringVar()`` is a *string* (i.e., typically some text)

Now the question is, how does *Python* know when to retrieve a
user-defined value? Typically, we want to evaluate user-defined values
when we call a function that receives user-defined values as input
arguments. Predefined, default values in a script can be set with
``VARIABLE.set()`` and  user settings can be retrieved with
``VARIABLE.get()``. The following code block features the usage of the
``get()``\ method (the
`script <https://github.com/hydro-informatics/material-py-codes/raw/master/gui/variable_gui.py>`__
and  the
`icon <https://github.com/hydro-informatics/material-py-codes/raw/master/gui/sample_icon.ico>`__
are available at the course repository).

.. code:: python

   from tkinter.messagebox import showinfo
   import rand om

   class MyApp(tk.Frame):
       def __init__(self, master=None):
           tk.Frame.__init__(self, master)

           self.master.title("GUI with variables")
           self.master.iconbitmap("gui/sample_icon.ico")

           # Set geometry: upper-left corner of the window
           ww = 628  # width
           wh = 100  # height
           wx = (self.master.winfo_screenwidth() - ww) / 2
           wy = (self.master.winfo_screenheight() - wh) / 2
           # assign geometry
           self.master.geometry("%dx%d+%d+%d" % (ww, wh, wx, wy))

           self.a_label = tk.Label(master, text="Enter a value to call:")
           self.a_label.grid(column=0, row=0, padx=5, pady=5)
           
           # define tk.StringVar() and  assign it to an entry
           self.user_entry = tk.StringVar()
           self.an_entry = tk.Entry(master, width=20, textvariable=self.user_entry)
           self.an_entry.grid(column=1, row=0, padx=5, pady=5)

           # define Button to trigger call back
           self.a_button = tk.Button(master, text="Call Message!", command =lambda: self.message_distributor())
           self.a_button.grid(column=2, row=0, padx=5, pady=5)

           # define a Checkbutton to use either user input or a rand om message
           self.check_variable = tk.BooleanVar()
           self.cbutton = tk.Checkbutton(master, text="Check this box to use a rand om message instead of the entry", variable=self.check_variable)
           self.cbutton.grid(sticky=tk.E, column=0, columnspan=3, row=1, padx=5, pady=5)
           self.check_variable.set(False)

           
       def message_distributor(self):
           if not self.check_variable.get():
               showinfo("User message", self.user_entry.get())
           else:
               showinfo("Rand om message", self.rand om_message())
           
       def rand om_message(self):
           rand om_words = ["summer", "winter", "is", "cold", "hot", "will be"]
           return " ".join(rand om.sample(rand om_words, 3))


   if __name__ == '__main__':
       MyApp().mainloop()

.. image:: ../../img/py-tk-variables.png  

.. _place-widget:

Design, place and  modify widgets
---------------------------------

The above code examples use both the ``OBJECT.grid()`` and  the
``OBJECT.pack()`` methods (geometry managers) to place widgets in the
GUI. There is one additional geometry manager in the form of the
``place`` method. Which of the geometry managers you want to use is
entirely up to you - there are pros and  cons for all geometry managers:

-  ``pack``

   -  automatically places widgets within a box
   -  works best for simple GUIs, where all widgets are in one column or
      row
   -  BUT complex layouts can only be hand led with complicated
      workarounds (i.e., do not use ``pack`` with a complex GUI)

-  ``place``

   -  places widgets at absolute or relative *x*-*y* positions
   -  works well for graphical arrangements of widgets

-  ``grid``

   -  places widgets in columns and  rows of a grid
   -  works well with table-like apps and  structured layouts

To enable more graphical flexibility, widgets accept many optional
keywords, for instance, to change their foreground (``fg``) or
background (``bg``) color. In addition, widgets can be modified with the
``tk.OBJECT.config(PARAMETER_TO_CONMFIGURE=NEW_CONFIG)`` method.

The following sections provide more details on the ``place`` and 
``grid`` geometry managers and  keyword arguments as well as widget
methods to modify widgets. Examples of the ``pack`` method are provided
with the above code blocks.

``place`` widgets and  use object colors
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The simplest geometry manager is the ``pack`` method, which works even
without any keyword provided as the very first examples on this page
illustrate. With the ``place`` method, widgets can be placed relatively
in the window (``relx`` and  ``rely``, where both must be < 1) or with
absolute positions (``x`` and  ``y``, where both should fit into the
window dimensions define with ``self.config(width=INT, height=INT)``).
The axis origin (zero positions of *x* and  *y*) are determined with the
``anchor`` keyword.

.. note::
   The parent frame still needs to be ``pack``-ed (``self.pack(...)``).

.. code:: python

   class PlacedApp(tk.Frame):
       def __init__(self, master=None, **options):
           tk.Frame.__init__(self, master, **options)
           self.pack(expand =True, fill=tk.BOTH)
           self.config(width=628, height=100)
           self.master.title("A placed GUI")
           tk.Label(self, text="Vanilla", bg="goldenrod", fg="dark slate gray").place(anchor=tk.NW, relx=0.2, y=10)
           tk.Label(self, text="Green green tree", bg="OliveDrab1").place(anchor=tk.E, relx=0.8, rely=0.5)
           tk.Label(self, text="Blue sky", bg="DeepSkyBlue4", fg="floral white").place(anchor=tk.CENTER, x=300, rely=0.8)


   if __name__ == '__main__':
       PlacedApp().mainloop()

.. image:: ../../img/py-tk-placed.png  

.. note::
   The above example does not create class objects of ``tk.Labels``, which makes the labels non-modifiable. This definition of widgets is acceptable to shorten long GUI scripts, but only if the widgets should not be modified later.

Place objects with ``grid``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In ``grid``-ed GUIs, the widget alignment can be controlled with the
``sticky`` argument that uses cardinal directions (e.g., ``sticky=tk.W``
aligns or *sticks* a widget to the west, i.e., left side of a GUI).
Moreover, the ``padx`` and  ``pady`` keywords arguments enable the
implementation of pixel space around widgets.

.. code:: python

   from tkinter.messagebox import showinfo

   class GriddedApp(tk.Frame):
       def __init__(self, master=None, **options):
           tk.Frame.__init__(self, master, **options)
           self.pack(expand =True, fill=tk.BOTH)
           self.config(width=628, height=100)
           self.master.title("A grid GUI")
           tk.Label(self, text="Enter name: ", bg="bisque2", fg="gray21").grid(sticky=tk.W, row=0, column=0, padx=10)
           tk.Entry(self, bg="gray76", width=20).grid(stick=tk.EW, row=0, column=1, padx=5)
           tk.Button(self, text="Show message", bg="pale turquoise", fg="red4", command =lambda: showinfo("Info", "Rand om message")).grid(row=0, column=2, padx=5)
           tk.Checkbutton(self, text="A Checkbutton over multiple columns").grid(stick=tk.E, row=1, column=0, columnspan=3, pady=15)


   if __name__ == '__main__':
       GriddedApp().mainloop()

.. image:: ../../img/py-tk-grid.png 

Configure widgets
~~~~~~~~~~~~~~~~~

Upon a user action (event), we may want to modify previously defined
widgets. For instance, we may want to change the text of a label or the
layout of a button to indicate successful or failed operations. For this
purpose, ``tkinter`` objects can be modified with
``tk.OBJECT.config(PARAMETER_TO_CONMFIGURE=NEW_CONFIG)``. Moreover,
objects can be delete (destroyed) with ``tk.OBJECT.destroy()``, even
though this is not an elegant method for any other widgets than pop-up
windows (child frames of the parent frame).

.. code:: python

   from tkinter.messagebox import showinfo, showerror

   class ReConfigApp(tk.Frame):
       def __init__(self, master=None, **options):
           tk.Frame.__init__(self, master, **options)
           self.config(width=628, height=100)
           self.pack()
           
           self.user_depth = tk.DoubleVar()
           self.kst = 40.0
           self.w = 5.0
           self.slope = 0.002
           
           
           self.master.title("A GUI that reconfigures its widgets")
           tk.Label(self, text="Enter flow depth (numeric, in meters): ", bg="powder blue", fg="medium blue").grid(sticky=tk.W, row=0, column=0, padx=10)
           tk.Entry(self, bg="alice blue", width=20, textvariable=self.user_depth).grid(stick=tk.EW, row=0, column=1, padx=5)
           self.eval_button = tk.Button(self, text="Estimate flow velocity", bg="snow2", fg="dark violet", command =lambda: self.call_estimator())
           self.eval_button.grid(row=0, column=2, padx=5)
           
       def call_estimator(self):
           try:
               flow_depth = float(self.user_depth.get())
           except tk.TclError:
               return showerror("ERROR", "Non-numeric value entered.")
           self.eval_button.config(fg="green4", bg="DarkSeaGreen1")
           showinfo("Result", "The estimated flow velocity is: " + str(self.estimate_u(flow_depth)))
           
       def estimate_u(self, h):
           try:
               return self.kst * h**(2/3) * self.slope**0.5
           except ValueError:
               showerror("ERROR: Bad values defined.")
               return None
           except TypeError:
               showerror("ERROR: Bad data types defined.")
               return None
           

   if __name__ == '__main__':
       ReConfigApp().mainloop()

.. image:: ../../img/py-tk-config.png

.. admonition:: Challenge

   (1) The roughness value varies from case to case. Can you implement a ``ttk.Combobox`` to let a user choose a *Strickler* *kst* roughness value between 10 and  85 (integers) and define the channel slope in a ``tk.Entry`` or a custom pop-up window (see below)?
   
   (2) The cross-section averaged flow velocity also depends on the cross-section geometry. Can you implement ``tkinter`` widgets to enable user definitions of the bank slope ``m`` and  channel base width ``w`` to calculate the hydraulic radius?


.. image:: ../../img/flowVariables_xs.png

Pop-up windows
--------------

Default messages from ``tkinter.messagebox``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The import of ``tkinter.messagebox`` provides some stand ard pop-up
windows such as:

-  ``showinfo(title=STR, message=STR)`` that prints an information
   message (see above examples).
-  ``showwarning(title=STR, message=STR)`` that prints a warning
   message.
-  ``showerror(title=STR, message=STR)`` that prints an error message
   (see above example).
-  ``askyesno(title=STR, message=STR)`` that returns ``False`` or
   ``True`` depending on a user???s answers to a *Yes-or-No* question.
-  ``askretrycancel(title=STR, message=STR)`` that returns ``False`` or
   ``True``, or re-attempts to run an event (function) depending on a
   user???s answers to a *Yes-or-No-or-Cancel* question.
-  ``askokcancel(title=STR, message=STR)`` that returns ``False`` or
   ``True`` depending on a user???s answers to an *OK-or-Cancel* question.
-  ``askretrycancel(title=STR, message=STR)`` that returns ``False`` or
   ``True``, or re-attempts to run an event (function) depending on a
   user???s answers to a *OK-or-Retry-or-Cancel* question.

Read more about default pop-up windows in the `Python
docs <https://docs.python.org/3.9/library/tkinter.messagebox.html>`__.

Top-level custom pop-ups
~~~~~~~~~~~~~~~~~~~~~~~~

The default windows may not always meet your needs, for instance, if you
want to invite users to enter a custom value. In this case, a
``tk.Toplevel`` object aids to produce a custom window. The below
example shows how a custom top-level pop-up window can be called within
a method. With the ``tk.Toplevel`` widget and  the ``tk.Frame`` (parent)
widgets, there are two frames now, where buttons, labels, or any other
``tkinter`` objects can be placed. The very first argument of any
``tkinter`` object created determines whether the object is placed in
the parent or the top-level frame. For example,
``tk.Entry(self).pack()`` creates an entry in the parent ``tk.Frame``,
and  ``tk.Entry(pop_up).pack()`` creates an entry in the child
``tk.Toplevel``.

.. code:: python

   from tkinter.messagebox import showwarning

   class PopApp(tk.Frame):
       def __init__(self, master=None, **options):
           tk.Frame.__init__(self, master, **options)
           self.config(width=628, height=50)
           self.pack()
           
           self.master.title("Custom pop-up GUI")
           self.pop_button = tk.Button(self, text="Open pop-up window", bg="cadet blue", fg="white smoke", command =lambda: self.new_window())
           self.pop_button.pack()
           
       def destroy_buttons(self):
           self.pop_button.destroy()
           self.p_button1.destroy()
           self.p_button2.destroy()        
           showwarning("Congratulations", "This app is useless now. Don't press red-ish buttons ...'")
           
       def new_window(self):
           pop_up = tk.Toplevel(master=self)
           # add two buttons to the new pop_up Toplevel object (window)
           self.p_button1 = tk.Button(pop_up, text="Destroy buttons (do not click here)", fg="DarkOrchid4",
                                      bg="HotPink1", command =lambda: self.destroy_buttons())
           self.p_button2 = tk.Button(pop_up, text="Close window", command =lambda: pop_up.quit())  
           self.p_button1.pack()
           self.p_button2.pack()


   if __name__ == '__main__':
       PopApp().mainloop()

.. image:: ../../img/py-tk-popup-custom.png  

File dialog (open ???)
~~~~~~~~~~~~~~~~~~~~

When a custom function???s argument is a file or file name, we most likely want the user to be able to select the file needed. The ```tkinter.filedialog`` <https://docs.python.org/3.10/library/dialog.html#module-tkinter.filedialog>`__ module provides methods to let a user choose general or specific file types. Specific file types can be defined with the ``filetypes=("Name", "*.ending")`` (or ``filetypes=("Name", "*.ending1;*.ending2;...")`` for multiple file types) keyword argument. The following example illustrates the usage of ``tkinter.filedialog``\ ???s ``askopenfilename``.

.. code:: python

   from tkinter.filedialog import askopenfilename
   from tkinter.messagebox import showinfo

   class OpenFileApp(tk.Frame):
       def __init__(self, master=None, **options):
           tk.Frame.__init__(self, master, **options)
           self.config(width=628, height=50)
           self.pack()
           
           self.master.title("GUI to open a file")
           
           self.pop_button = tk.Button(self, text="Open a text file", bg="light steel blue", fg="dark slate gray", command =lambda: self.open_file())
           self.pop_button.pack()
           
       def open_file(self):
           file_types = (("Text", "*.txt;*.csv;*.asc"),)  # equivalent to [("Text", "*.txt;*.csv;*.asc")]
           file_name = askopenfilename(initialdir=".", title="Select a text file", filetypes=file_types, parent=self)
           showinfo("File info", "You selected " + str(file_name))


   if __name__ == '__main__':
       OpenFileApp().mainloop()

.. image:: ../../img/py-tk-filedialog.png 

Quit
----

To cleanly quit a GUI, use ``tk.Frame.quit()`` (i.e., in a customized class, use ``self.quit()`` or ``master.quit()``). The above example of the ``PopApp`` class also features the ``destroy()`` method, which can remove particular widgets.

``tkinter`` provides many more options such as the implementation of tabs with ``ttk.Notebook()`` (requires `binding <https://effbot.org/tkinterbook/tkinter-events-and -bindings.htm>`__ of tab objects), tables (``from tkintertable import TableCanvas, TableModel``), or interactive graphic objects with ``matplotlib``. To use ``tkinter`` with ``matplotlib``, add the following code block to the file header and create ``matplotlib`` objects as children of ``tkinter`` windows.

.. code:: python

   import matplotlib
   matplotlib.use('TkAgg')
   import numpy as np
   from matplotlib.backends.backend_tkagg import FigureCanvasTkAgg
   from matplotlib.figure import Figure

Enjoy creating your own apps!

.. admonition:: Exercise

   Get familiar with creating GUIs and object orientation in the `GUI <ex_gui.html>`__ exercise.
