Manning-Strickler formula
=========================

.. admonition:: Goals

   Write basic script and use loops. Write a function and parse optional keyword arguments (``**kwargs``).

.. admonition:: Requirements

   *Python* libraries: *math* (standard library). Read and understand how `loops <https://hydro-informatics.github.io/hypy_pyloop.html>`__ and `functions <https://hydro-informatics.github.io/hypy_pyfun.html>`__ work in *Python*.

Get ready by cloning the exercise repository:

::

   git clone https://github.com/Ecohydraulics/Exercise-ManningStrickler.git 

|rhone|\  *The Rhone River in Switzerland (source: Sebastian Schwindt 2014).* 

The theory
----------

The `Gauckler-Manning-Strickler formula <https://en.wikipedia.org/wiki/Manning_formula>`__ (or *Strickler formula* in Europe) relates water depth and flow velocity of open channel flow based on the assumption of one-dimensional (cross-section-averaged) flow characteristics. The *Strickler formula* results from a heavy simplification of the `Navier-Stokes <https://en.wikipedia.org/wiki/Navier-Stokes_equations>`__ and the `continuity <https://en.wikipedia.org/wiki/Continuity_equation>`__ equations. Even though one-dimensional (1D) approaches have largely been replaced by at least two-dimensional (2d) numerical models today, the 1d Strickler formula is still frequently used as a first approximation for boundary conditions.

The basic shape of the *Strickler formula* is:

*u = kst· S1/2 · Rh2/3* 

where:

-  *u* is the cross-section-averaged flow velocity in (m/s)
-  *kst* is the *Strickler* coefficient in *fictional* (m1/3/s)
   corresponding to the inverse of `Manning’s    n <http://www.fsl.orst.edu/geowater/FX3/help/8_Hydraulic_Reference/Mannings_n_Tables.htm>`__.
  
	-   *kst* ≈ 20 (*n*\ ≈0.05) for rough, complex, and near-natural rivers   
	-   *kst* ≈ 90 (*n*\ ≈0.011) for smooth, concrete-lined channels   
	-   *kst* ≈ 26/*D901/6* (approximation based on the grain size *D90*, where 90% of the surface sediment grains are smaller, according to `Meyer-Peter and Müller 1948 <http://resolver.tudelft.nl/uuid:4fda9b61-be28-4703-ab06-43cdc2a21bd7>`__)

-  *S* is the hypothetic energy slope (m/m), which can be assumed to correspond to the channel slope for steady, uniform flow conditions.
-  *Rh* is the hydraulic radius in (m)

The hydraulic radius *Rh* is the ratio of wetted area *A* and wetted perimeter *P*. Both *A* and *P* can be calculated as a function of the water depth *h* and the channel base width *b*. Many channel cross-sections can be approximated with a trapezoidal shape, where the water surface width *B*\ =\ *b+2·h·m* (with *m* being the bank slope as indicated in the figure below).

.. figure:: https://github.com/Ecohydraulics/media/raw/master/png/flow-cs.png    
	:alt: FlowCrossSection 

   

Thus, *A* and *P* result from the following formulas:

-  *A = h · 0.5·(b + B) = h · (b + h·m)*
-   *P = b + 2h·(m² + 1)1/2* 

Finally, the discharge *Q* (m³/s) can be calculated as: *Q = u · A = kst · S1/2· Rh2/3 · A* 

Calculate the discharge
-----------------------

Write a script that prints the discharge as a function of the channel base width *b*, bank slope *m*, water depth *h*, the slope *S*, and the *Strickler* coefficient *kst*.

.. tip::
   Use ``import math as m`` to calculate square roots (``m.sqrt``). Powers are calculated with the ``**`` operator (e.g., *m²* corresponds to ``m**2``).

Functionalize
-------------

Cast the calculation into a function (e.g., ``def calc_discharge(b, h, k_st, m, S): ...``) that returns the discharge *Q*.

Flexibilize
-----------

Make the function more flexible through the usage of optional keywords arguments (```**kwargs`` <https://hydro-informatics.github.io/hypy_pyfun.html#keyword-arguments-kwargs>`__) so that a user can optionally either provide the *D90* (``D90``), the *Strickler* coefficient *kst* (``k_st``), or *Manning’s n* (``n_m``)

.. tip::
   Internally, use only *Manning’s n* for the calculations and parse ``kwargs.items()`` to find out the ``kwargs`` provided by a user.

Invert the function
-------------------

The backward solution to the *Manning-Strickler* formula is a non-linear problem if the channel is not rectangular. This is why an iterative approximation is needed and here, we use the *Newton-Raphson* scheme for this purpose. More literature about the *Newton-Raphson* scheme is provided on ILIAS.

.. tip::
   The absolute value of a parameter can be easily accessed through the built-in ``abs()`` method in *Python3*.

Use a Newton-Raphson solution scheme (`Paine 1992 <https://doi.org/10.1061/(ASCE)0733-9437(1992)118:2(306)>`__) to interpolate the water depth ``h`` for a given discharge *Q* of a trapezoidal channel.

Write a new function ``def interpolate_h(Q, b, m, S, **kwargs):``

-  Define an initial guess of ``h`` (e.g., ``h = 1.0``) and an initial error margin (e.g., ``eps = 1.0``)
-  Use a ``while`` loop until the error margin is negligible small (e.g., ``while eps > 10**-3:``) and calculate the :
  
	-   wetted area ``A`` (see above formula)  
	-   wetted perimeter ``P`` (see above formula)  
	-   current discharge guess (based on ``h``):
		  ``Qk = A**(5/3) * sqrt(S) / (n_m * P**(2/3))``   
	-   error update ``eps = abs(Q -  Qk) / Q``   
	-   derivative of ``A``: ``dA_dh = b + 2 * m * h``   
	-   derivative of ``P``: ``dP_dh = 2 * m.sqrt(m**2 + 1)``   
	-   function that should become zero ``F = n_m * Q * P**(2/3) -  A**(5/3) * m.sqrt(S)``   
	-   its derivative:
		  ``dF_dh = 2/3 * n_m * Q * P**(-1/3) * dP_dh -  5/3 * A**(2/3) * m.sqrt(S) * dA_dh``   
	-  a water depth update ``h = abs(h - F / dF_dh)`` 

-  Implement an emergency stop to avoid endless iterations -  the Newton-Raphson scheme is not always stable!
-  Return ``h`` and ``eps`` (or calculated discharge ``Qk``)

.. |rhone| image:: https://github.com/Ecohydraulics/media/raw/master/jpg/hydraulics-1d.jpg 