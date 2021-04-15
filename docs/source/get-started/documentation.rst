Documentation
=============

Leonardo Da Vinci used journals to sketch, develop and eventually pass on his ideas. Alexand er von Humboldt documented many of his journeys in travel journals and Marie Skłodowska Curie wrote down the theory of “radioactivity” using pens and papers. Today, writing media have evolved into infinite digital oceans with sophisticated tools for documenting code and ideas. Also the way in which we look for and retrieve information has evolved from searching for lexicon entries to using keywords in search engines. So if you have made an ingenious discovery, you want to make sure you document it well so that others can understand 
and use it. You also want to make sure that others can find your stroke of genius in digital media. You also want to make sure that others can find your stroke of genius in digital media. One of the most widespread methods for documenting and spreading ideas is the use of so-called wikis (from Hawaiian: *fast*), which can easily be written in markdown language. *GitHub* provides comprehensive, easy-to-read explanations for `project documentation <https://guides.github.com/features/wikis/>`__ with *Markdown* as core element. This page presents the basics of the markdown language to leverage wikis. Moreover, the powerful alternative of using *reStructuredText* in *Sphinx*-based documentations is introduced.

.. tip::
   `Write the Docs <https://www.writethedocs.org/guide/writing/beginners-guide-to-docs/>`__ provides comprehensive guides for code documentation
-  just take about 10 minutes to read how to save days.

What to document?
-----------------

A good code documentation starts with a qualitative and concise description of software (e.g., a *Python* package) capacities, products, and requirements. It also provides workflows for installing and using the software, at best with illustrative examples. Finally, a good troubleshooting section enables users to find problems in their data setup or software usage. To enable future development and maintenance, a *Contributing* section provides *good-practice-guidelines* for coding new software capacities.

Present the software
~~~~~~~~~~~~~~~~~~~~

This section intends to advertise the benefits and capacities of the software: Tell users briefly the purpose of the software, why it is unique and what it produces.

Requirements
~~~~~~~~~~~~

This section should answer the following questions:

-  What system requirements are needed?
-  Which dependencies does the software have (e.g., other *Python*    packages such as *NumPy*)?
-  What input data does a user need to run the software?

Installation
~~~~~~~~~~~~

Describe step-by-step the installation of the software (e.g., how to download and access your *Python* package). Screenshots can be helpful here. At best, the *Requirements* section made it clear what users need to proceed with the installation.

Usage
~~~~~

Describe how the software can be used, starting with basics such as importing the software as *Python* package. Mention possible pre- and 
post-processing for input and output data, respectively. If available, add more complex functionalities consecutively in a logical order.

To truly make your software useful to others, add a case study. Most users will not read the detailed code documentation until they get the software to run once and see what it can do. A use case also helps to check the logic of your code and gives users the opportunity to bridge imperfect code documentation sections to their workflow. This can sometimes be necessary, even if your code is certainly perfect and the documentation is foolproof.

Troubleshooting
~~~~~~~~~~~~~~~

Sure, your code is error-free and of course only the user makes mistakes. Show compassion and integrate specific *try*-*except* statements (more on the `Python\ basics <hypy_pyerror.html#try-except>`__ page) in the source code, which point out possible error sources. These error (and maybe even warning) messages should all be listed in a *Troubleshooting* section of the code documentation. Any source of error (message) should be documented regarding the following aspects:

-  Cause: Possible reasons for why an error occurs.
-  Remedy: Steps for troubleshooting an error.

Contributing
~~~~~~~~~~~~

Your software is brilliant. To make the software even more brilliant, foolproof, and powerful, it is a great idea (actually: an absolute must)
to get more authors on the development team. However, it is very likely that any other author has individual preferences when it comes to code stand ards. So make sure to set up clear rules for other contributors from the beginning. For example, define clear code conventions as explained on the `code style <hypy_pystyle.html>`__ page.

Markdown 
--------

*Markdown* was created in 2004 and is a simple markup language that is intuitive and easy to learn. Markup languages structure the content of plain text documents regarding the way a document is displayed to end users (rich text format). Other popular markup languages are for example `TeX <https://en.wikipedia.org/wiki/TeX>`__ and `XML (Extensible Markup Language) <https://en.wikipedia.org/wiki/XML>`__. *Markdown* became a popular tool for writing syntactically distinguishable computer text that is then translated into rich text. Here is an example how *Markdown* works:

.. code:: markdown 

   # Better than Word-like rich text editors 
   *OS*-independent functionality:
  
	-  Avoid formatting of the same kind of thing redundantly (and inconsistently)	  
	-  Backwards compatibility   
	-  Formulae handling 	  
	-  ... and many more ... 

--------------

**Better than Word-like rich text editors** *OS*-independent functionality:
-  Avoid formatting of the same kind of thing redundantly (and inconsistently)
-  Backwards compatibility
-  Formulae handling
-  ... and many more ...



Markdown Editors (IDEs)
~~~~~~~~~~~~~~~~~~~~~~~

Many text editors provide *Markdown* add-ons and *Markdown*-only editors are loosing their significance more and more. Editors that simultaneously support *Markdown* and programming languages like *Python* or *R* are state of the art and therefore recommended.

Basic text editors that support *Markdown* are listed `here <hy_others.html#npp>`__. Popular and multi-platform *IDE*\ s for editing *Markdown* (``.md``) files are `ATOM <https://atom.io/>`__ (for combination with *JavaScript*, *html*, and *CSS*), and `Jupyter Lab <https://jupyter.org>`__ or `PyCharm <https://www.jetbrains.com/pycharm/>`__ (for combination with *Python* or *R*), which both are available through `Anaconda <https://docs.conda.io/>`__. `Read more about Anaconda and 
associated IDE\ s on the previous pages. <hy_ide.html>`__ 
Markdown command overview (+images)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following table and sections provide an overview of basic markdown command s. There is much more options out there, which you can find by using your favorite search engine with the keywords ``markdown`` ``guide``.

+----------------------+------------------------------+----------------+
| Feature              | Code                         | Example        |
+======================+==============================+================+
| Blockquote           | ``|     A quote``            | ``|`` A quote  |
+----------------------+------------------------------+----------------+
| Bold text            | ``**Bold**``                 | **Bold**       |
+----------------------+------------------------------+----------------+
| Code block (inline)  | ``inline``                   | inline         |
|                      | :literal:`\`code\``          | :lite          |
|                      |                              | ral:`\`code\`` |
+----------------------+------------------------------+----------------+
| Heading 1            | ``# Heading 1``              | **Heading 1**  |
+----------------------+------------------------------+----------------+
| Heading 2            | ``## Heading 2``             | **Heading 2**  |
+----------------------+------------------------------+----------------+
| Heading 3            | ``### Heading 3``            | **Heading 3**  |
+----------------------+------------------------------+----------------+
| Horizontal rule      | ``***`` or ``===``           | ——-            |
+----------------------+------------------------------+----------------+
| Hyperlink            | ``[Lin                       | `Link          |
|                      | k](https://fruitsinfo.com)`` |  <https://frui |
|                      |                              | tsinfo.com>`__ |
+----------------------+------------------------------+----------------+
| Hyperlink to section | ``[Link](http                | `Link to       |
|                      | s://fruitsinfo.com)#apples`` | apple-section  |
|                      |                              |  <https://frui |
|                      |                              | tsinfo.com>`__ |
+----------------------+------------------------------+----------------+
| Image                | ``![ImgName](https:          | |ImgName|      |
|                      | //image-address/image.png)`` |                |
+----------------------+------------------------------+----------------+
| Italic text          | ``*italic*``                 | *italic*       |
+----------------------+------------------------------+----------------+
| Numbered list item   | ``1. numbered item``         | 1. Numbered    |
|                      |                              | item           |
+----------------------+------------------------------+----------------+
| Reference (defined)  | `                            | `Defined       |
|                      | `[Defined Reference][wiki]`` | Referenc       |
|                      |                              | e <https://wik |
|                      |                              | ipedia.org>`__ |
+----------------------+------------------------------+----------------+
| Reference            | ``[wi                        | *Place at file |
| (definition)         | ki]: https://wikipedia.org`` | bottom*        |
+----------------------+------------------------------+----------------+
| Strikethrough        | ``~~Strikethrough~~``        | [STRIKEOUT:    |
|                      |                              | Strikethrough] |
+----------------------+------------------------------+----------------+

Itemization (un-numbered list)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Itemized list section can be produced using ``*``, ``+``, or ``-`` symbols with tabs that determine the list indentation:

.. code:: markdown 

   * level 1 item 
		-  level 2 item       
		-  another level 2 item
			+ level 3 item
   * next level 1 item 

--------------

   * level 1 item 
		-  level 2 item       
		-  another level 2 item
			+ level 3 item
   * next level 1 item 

--------------

Tables
~~~~~~

Table columns are separated by a ``|`` sign. The first row determines row headers and the second row the alignment through the use of ``:`` (see below example).

.. code:: markdown 

   | Fruit | Kingdom | Genus |
   |-------|:-------:|------:|
   |Banana | Plantae | Musa |
   |Jackfruit|Plantae|Artocarpus|

--------------

========= ======= ==========
Fruit     Kingdom Genus
========= ======= ==========
Banana    Plantae Musa 
Jackfruit Plantae Artocarpus
========= ======= ==========

--------------

Converting complex tables from workbooks (e.g., from *LibreOffice Calc* or *MS Excel*) is possible with many online tools and here is just one example from Dave Johnson:
`https://thisDaveJ.com <https://thisdavej.com/copy-table-in-excel-and -paste-as-a-markdown-table/>`__.

Math expressions: Equations
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Math expressions and equations must be implemented as text in stand ard *Markdown*. *GitHub*\ s markdown interpreter does not support many external *TeX*-like equation renderers for reasons of security. However, *GitHub* users can still render *TeX*-like equations with the following code:

.. code:: html 

   <img src="https://render.githubusercontent.com/render/math?math=sin{\alpha} = \sqrt{1-cos^{2}\alpha}">



Note that the equation starts after ``math&math=``. Thus, for using the math snippet in a document, copy and modify the following expression ``<img src="https://render.githubusercontent.com/render/math?math=TYPE =  EQUATION HERE">``.

html -  markdown
~~~~~~~~~~~~~~~~

*html* structures can be flawlessly used in *Markdown*, which itself is nothing else than simplified *html*. Therefore, any *html* structure can be used within markdown and the above-shown equation implementation already represents the first example for *html* usage in a *Markdown* document. The following sections provide an overview of some more or less frequently used *html* symbols that also work with *Markdown*.

Math expressions: Greek letters
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to use greek letters in inline text, use *html* language, where ``&lettername;`` produces the desired *Greek* letter symbol (e.g., type ``&delta;`` to output δ or ``&Delta;`` to output a capital letter Δ).
The following table provides an overview of Greek letter symbols.

====== ============= ====== =============
Letter Code          letter code 
====== ============= ====== =============
Α      ``&Alpha;``   α      ``&alpha;`` 
Β      ``&Beta;``    β      ``&beta;`` 
Γ      ``&Gamma;``   γ      ``&gamma;`` 
Δ      ``&Delta;``   δ      ``&delta;`` 
Ε      ``&Epsilon;`` ε      ``&epsilon;`` 
Ζ      ``&Zeta;``    ζ      ``&zeta;`` 
Η      ``&Eta;``     η      ``&eta;``
Θ      ``&Theta;``   θ      ``&theta;`` 
Ι      ``&Iota;``    ι      ``&iota;`` 
Κ      ``&Kappa;``   κ      ``&kappa;`` 
Λ      ``&Lambda;``  λ      ``&lambda;`` 
Μ      ``&Mu;``      μ      ``&mu;`` 
Ν      ``&Nu;``      ν      ``&nu;`` 
Ξ      ``&Xi;``      ξ      ``&xi;`` 
Ο      ``&Omicron;`` ο      ``&omicron;`` 
Π      ``&Pi;``      π      ``&pi;`` 
Ρ      ``&Rho;``     ρ      ``&rho;`` 
Σ      ``&Sigma;``   σ      ``&sigma;`` 
Τ      ``&Tau;``     τ      ``&tau;`` 
Υ      ``&Upsilon;`` υ      ``&upsilon;`` 
Φ      ``&Phi;``     φ      ``&phi;`` 
Χ      ``&Chi;``     χ      ``&chi;`` 
Ψ      ``&Psi;``     ψ      ``&psi;`` 
Ω      ``&Omega;``   ω      ``&omega;`` 
====== ============= ====== =============

Math expressions: Arrows and Operators
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Arrows and operators can also be implemented as *html* symbols. The following table provides an overview.

=============== =============== ============== ===============
  Arrows        Operators (1)    Operators (2)    Operators (3)
=============== =============== ============== ===============
←  ``&larr;``   ∀ ``&forall;``   ∗ ``&lowast;``   ∼ ``&sim;`` 
↑  ``&uarr;``   ∂ ``&part;``     √ ``&radic;``    ≅ ``&cong;`` 
→  ``&rarr;``   ∃ ``&exist;``    ∝ ``&prop;``     ≈ ``&asymp;`` 
↓  ``&darr;``   ∅ ``&empty;``    ∞ ``&infin;``    ≠ ``&ne;`` 
↔  ``&harr;``   ∇ ``&nabla;``    ∠ ``&ang;``      ≡ ``&equiv;`` 
↵  ``&crarr;``  ∈ ``&isin;``     ∧ ``&and ;``      ≤ ``&le;`` 
⇐  ``&lArr;``   ∉ ``&notin;``    ∨ ``&or;``       ≥ ``&ge;`` 
⇑  ``&uArr;``   ∋ ``&ni;``       ∩ ``&cap;``      ⊂ ``&sub;`` 
⇒  ``&rArr;``   ∏ ``&prod;``     ∪ ``&cup;``      ⊃ ``&sup;`` 
⇓  ``&dArr;``   ∑ ``&sum;``      ∫ ``&int;``      ⊄ ``&nsub;`` 
⇔  ``&hArr;``   − ``&minus;``    ⋅ ``&sdot;``     ⊥ ``&perp;`` 
=============== =============== ============== ===============

Miscellaneous Symbols
~~~~~~~~~~~~~~~~~~~~~

*Markdown* profits from many more *html* symbols that may be used in equations or other text. The following table provides an overview over such miscellaneous symbols.

== ============ = ============ = =============
\  Symbols (1)     Symbols (2)     Symbols (3)
== ============ = ============ = =============
"  ``&quot;``   – ``&ndash;``  ‾ ``&oline;`` 
&  ``&amp;``    — ``&mdash;``  ⁄ ``&frasl;`` 
<  ``&lt;``     ‘ ``&lsquo;``  ς ``&sigmaf;`` 
>  ``&gt;``     ’ ``&rsquo;``  ℑ ``&image;`` 
Œ  ``&OElig;``  ‚ ``&sbquo;``  ℜ ``&real;`` 
œ  ``&oelig;``  “ ``&ldquo;``  ™ ``&trade;`` 
Š  ``&Scaron;`  ” ``&rdquo;``  ℵ ``&alefsym;`` 
š  ``&scaron;`` „ ``&bdquo;``  ⌈ ``&lceil;`` 
Ÿ  ``&Yuml;``   † ``&dagger;`` ⌉ ``&rceil;`` 
ˆ  ``&circ;``   ‡ ``&Dagger;`` ⌊ ``&lfloor;`` 
˜   ``&tilde;``  ‰ ``&permil;`` ⌋ ``&rfloor;``
   ``&ensp;``   ‹ ``&lsaquo;`` ⟨ ``&lang;`` 
   ``&emsp;``   › ``&rsaquo;`` ⟩ ``&rang;`` 
   ``&thinsp;`` € ``&euro;``   ◊ ``&loz;`` ‌
   ``&zwnj;``   • ``&bull;``   ♠ ``&spades;`` 
   ``&zwj;``    … ``&hellip;`` ♣ ``&clubs;`` ‎
   ``&lrm;``    ′ ``&prime;``  ♥ ``&hearts;`` ‏ 
   ``&rlm;``    ″ ``&Prime;``  ♦ ``&diams;`` 
== ============ = ============ = =============

Wikis 
-----

While every `git <hy_git.html>`__ repository should at least contain a descriptive *README.md*, *wiki*\ s provide much more detail and 
guidance. Wikis are a convenient way to guide users with permanent side bars (such as the menu bar on this web site), help users to understand 
methods and codes, and collaborative coding with precise descriptions of scripts. *GitHub* users find options to activate *wiki*\ s in the *Settings* tab of a repository and the developers continue to improve *wiki* functions (`read more about GitHub\ ’s wikis <https://help.github.com/en/github/building-a-strong-community/about-wikis>`__).

More sophisticated *wiki*\ s are available on the *Jekyll* themes web site (e.g., the `git-wiki theme <https://jekyll-themes.com/git-wiki/>`__). In order to use *Jekyll* themes, make sure to enable `GitHub pages <https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site>`__ (in the repository *Settings* tab) for the repository where you want to establish the *wiki* (this wiki-repository is typically another repository in order to describe a code-repository). Then, install the *Ruby development environment* and *Jekyll* (see `instructions on their website <https://jekyllrb.com/docs/>`__) in order to access and build hundreds of themes for code and project documentation. Forked and 
locally adapted themes can then be *push*\ ed to a remote *wiki* repository using `git <hy_git.html>`__.

.. tip::
   There are other git-pages and wiki host providers out there, such as `GitLab <https://gitlab.com/pages>`__ or `plan.io <https://plan.io/knowledge-management/>`__.

.. admonition:: Exercise

   Get practice in markdown with the `markdown & git <ex_git.html>`__ exercise.

*reStructuredText*, *Sphinx* and readthedocs
--------------------------------------------

An alternative to markdown is `reStructuredText <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>`__ that enables embedding *Python* *docstrings* (`read more in the code style conventions <hypy_pystyle.html>`__) of any script or module with `Sphinx <https://www.sphinx-doc.org>`__.

Without any *Python* or programming knowledge, it might be hard to get started with *Sphinx*. So make sure to understand *Python* basics and 
document any code with *docstrings*, at best using `google style <https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_google.html>`__ formatting. Once you start documenting your first *Python* package, *google-style* *docstrings* will enable the fast generation of high-quality docs. Currently, one of the best options for partially auto-generating code documentations, for any programming language, is `readthedocs <https://readthedocs.org/>`__, which builds on *Sphinx* and 
*reStructuredText*.

.. |ImgName| image:: https://raw.githubusercontent.com/RiverArchitect/Media/master/images/logo_small.ico 