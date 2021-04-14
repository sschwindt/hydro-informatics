.. _npp:

NotepadPlusPlus
---------------

`Notepad++ <https://notepad-plus-plus.org/>`__ is an all-round text
editor for basic coding (*R*, *Python*, *Java*, *C*, *Perl*, …),
markdown/html editing and many many (not a typo). Alternatives for
*Notepad++* are for example `ATOM <https://atom.io/>`__,
`Vim <https://www.vim.org/>`__ or `GNU
Emacs <https://www.gnu.org/software/emacs/>`__.

.. _lo:

Libre Office (MS Office alternative)
------------------------------------

An office software such as
`LibreOffice <https://www.libreoffice.org/>`__ or Microsoft’s *Excel* is
required for some of the analyses described on these pages.

.. _octave:

GNU Octave (Matlab® alternative)
--------------------------------

*Matlab*\ ® is nowadays established as one of the leading tools in
science and engineering. However, license fees and its proprietary
nature limit the use of *Matlab*\ ® to privileged entities and users.
Good news, there is a remedy in the shape of `GNU
Octave <https://www.gnu.org/software/octave/>`__. *GNU Octave* and
*Matlab*\ ® use very similar syntax and ``.m`` files can be run with
both programs. If error messages occur by running a ``.m`` file with
*GNU Octave*, make sure to load relevant packages at the top of the
script (this is one of the major differences between *GNU Octave* and
*Matlab*\ ®). For example:

::

   pkg load io
   # ... some script with console output
   pkg unload io

All stable *GNU Octave* packages can be found one their
`website <https://octave.sourceforge.io/packages.php>`__. To install one
of these packages, open *GNU Octave* and type in the command window:

::

   pkg install -forge new_package  # installs the package
   pkg load new_package  # loads the package in the active session

Afterwards, the new package can be loaded anytime by just typing in
``pkg load new_package``. For example, the following code snippet
installs and loads the ``video`` package:

::

   pkg install -forge video
   pkg load video

{% include tip.html content=“*Python* provides comes with many more
options for data processing and analyses. So instead of trying to tweak
*Matlab*\ ® code, consider reading and using the `Python tutorial with
its NumPy package <hypy_pynum.html#numpy>`__ descriptions. The tutorial
also highlights the `differences between Matlab\ ® and Python\ ’s
NumPy <hypy_pynum.html#can-numpy-do-matlab>`__ notation.” %}

*MATLAB® is a registered trademark of The MathWorks.*
