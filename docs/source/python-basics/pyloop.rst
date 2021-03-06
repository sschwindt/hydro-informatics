Loops and Conditional Statements
================================

Summary: IIterate and apply conditional criteria.

The *html* version of this notebook is hosted at
https://hydro-informatics.github.io/hypy_pyloop.html.

*Python* provides two basic types of loops to iterate through objects or
functions: the ``for`` and the ``while`` loop statements. Both loop
types have additional options and can be combined with conditional
statements. Conditional statements evaluate *boolean* arguments
(``True``/``False``) using the keywords ``if: ... else: ...``. This
section introduces the two loop types and conditional statements as
integral parts of loops.

Conditional statements (``if`` - ``else``)
------------------------------------------

Conditional statements open with an ``if`` keyword, followed by a test
condition (e.g., ``variable >= 2``) and action to accomplish when the
test condition is ``True``
(`boolean <https://hydro-informatics.github.io/hypy_pybase.html#boolean>`__
test result). The conditional statement can be followed by the ``elif``
(*else if*) and/or ``else`` keywords, which represent alternative tests
in the case that the ``if`` test-condition was ``False``. However, when
the ``if`` statement was ``True``, none of the following statements will
be evaluated.

.. code:: ipython3

    variable_2_test = "ice cream"
    if "cream" in variable_2_test:
    	print("It's creamy, for sure.")
    elif "ice" in variable_2_test:
        print("It's cold, ice-cold cream.")
    else:
    	print("Anything but ice cream.")
    


.. parsed-literal::

    It's creamy, for sure.
    

Any operator can be used in the test condition (see
`operators <https://hydro-informatics.github.io/hypy_pybase.html#operators>`__)
and conditions can be nested, too. > **Note**: The code blocks in the
``if`` - ``else`` statement is indented and *Python* uses the
indentation to group statements. The same applies to loops, function and
classes. An IDE automatically indents code, but basic text editors may
not do the job. So be aware that wrong indentation can be an error
source.

.. code:: ipython3

    number_of_scoops = 3
    if number_of_scoops <= 0:
    	print("Why? How can you?")
    elif number_of_scoops < 4:
        if number_of_scoops == 1: # this is a nested if-statement
            print("One is better than nothing.")
        else:
            print("That is reasonable.")
    else:
    	print("A lot. Still reasonable. Maybe.")


.. parsed-literal::

    That is reasonable.
    

``for`` loop
------------

``for`` loops serve for the sequential iteration through objects such as
lists or arrays. ``for`` loops can also be complemented with ``else``
statements at the end (why ever you want to do this???).

.. code:: ipython3

    for e in range(0,8,2):
    	print("e is %d now." % e)
    
    flavors = ["chocolate", "bread", "cherry"] 
    for index in range(len(flavors)): 
        print(flavors[index])
    else:
        print(" --- end of first loop.")
        
    # produces the same
    for e in flavors:
        print(e)


.. parsed-literal::

    e is 0 now.
    e is 2 now.
    e is 4 now.
    e is 6 now.
    chocolate
    bread
    cherry
     --- end of first loop.
    chocolate
    bread
    cherry
    

In many cases it is useful to use not only either the iteration step
(e.g., as an incrementing *integer* value) or the elements of a list
(e.g., a *string* value), but both simultaneously. Both iteration step
and list elements can be accessed with the ``enumeration`` method:

.. code:: ipython3

    for iteration_step, list_element in enumerate(flavors):
        print("The list element {0} is at position number {1}.".format(list_element, str(iteration_step)))


.. parsed-literal::

    The list element chocolate is at position number 0.
    The list element bread is at position number 1.
    The list element cherry is at position number 2.
    

``while`` loop
--------------

``while`` loops run until a certain test condition (expression) is met.
Similar to the ``if`` statement, the test condition can be composed by
just one variable or an expression including
`operators <https://hydro-informatics.github.io/hypy_pybase.html#operators>`__
(e.g., ``while a > b``). In order to modify a variable within a
``while`` loop, use ``+=`` (add ammount), ``-=`` (substract amount),
``*=`` (multiply with), or ``/=`` (divide by). Also ``while``\ loops can
be complemented with ``else`` statements. > **Warning**: Make sure that
every ``while`` loop has some ``break`` statement - otherwise, the
script may be caught in an endless loop.

.. code:: ipython3

    count = 10
    while (count > 7):
        count -= 1
        print("Count down %d " % count)
    else:
        print("Mission aborted.")
    
    count = 0
    while True:
    	print("Count up: %d " % count)
    	count += 1 # Replaces count = count + 1 - also works with -=, *= and /=
    	if count > 3:
    		break


.. parsed-literal::

    Count down 9 
    Count down 8 
    Count down 7 
    Mission aborted.
    Count up: 0 
    Count up: 1 
    Count up: 2 
    Count up: 3 
    

Example
-------

Use this code block to practice with data types, ``for`` loops and
conditional ``if`` statements by modifying the variables ``scoops`` and
``favorite_flavor``. Note the implementation of ``try`` and ``except``
key words, which ensure that whatever number of ``scoops`` or
``favorite_flavor`` you define will not crash the script.

.. code:: ipython3

    scoops = 2 # re-define the number of sccops
    favorite_flavor = "vanilla" # choose your favorite flavor
    
    size_scoops = {1: "small", 2: "medium", 3: "this is too much ice cream"}
    price_scoops = {1: "3 dollars", 2: "5 dollars", 3: "your health"}
    print("Hi,\nI want %d scoop-s in a waffle, please." % scoops)
    
    try:
        size = " " + str(size_scoops[scoops])
        price = str(price_scoops[scoops])
    except ValueError:
        size = "n unavailable number of scoops"
        price = "not defined"
    
    
    print("My pleasure to serve you. You have chosen a" + size + " ice cream. The price is " + price + ".")
    print("Let me guess your favorite flavor. Say stop when I \'m correct.")
    for f in flavors:
        print("I guess your favorite flavor is %s." % f)
        if f == favorite_flavor:
            print("Stop, that\'s it!")
            if f == "bread":
                print("Sorry, this is not a bakery.")
            break 
    


.. parsed-literal::

    Hi,
    I want 2 scoop-s in a waffle, please.
    My pleasure to serve you. You have chosen a medium ice cream. The price is 5 dollars.
    Let me guess your favorite flavor. Say stop when I 'm correct.
    I guess your favorite flavor is chocolate.
    I guess your favorite flavor is bread.
    I guess your favorite flavor is cherry.
    

   **Exercise:** Practice the application of loops with the `Hydraulics
   (1D) <ex_ms.html>`__ exercise.
