
.. warning::
    This is an unconventional mechanism, so this should be considered experimental, and is extra likely to change before Mango 1.0.

Argument passing
===============================

To cut right to the point: Mango passes argument by reference when calling functions. Keep reading to learn more!

By value vs by reference
---------------------------

There are two common ways to 'move' variables, for example when calling a function. They are:

* **As values**, which are passed by copying their value. This is for example the case with primitives in Java, or structs on the stack in C.
* **By reference**, which are passed around by copying only the pointer to the actual data. This is for example the case with Fortran or Perl, and when requested in C++ (``&``).

But while most languages technically copy values, it can look a lot like they pass by reference! That's because a lot of variables are just references/pointers to data. The references get copied, but the data does not.

This is for example the case with everything in Python, objects in Java, and heap-allocated structs in C.

In some cases, this makes no semantic difference (even if it might affect performance). But sometimes it does:

.. code-block::

    fn update_list(x: List<Int>):
        x = [2 * x[0]]
    fn update_number(x: List<Int>):
        x[0] = x[0] * 2

    let li1 = [1]
    update_list(li1)
    print(li1)

    # list with one element
    let li2 = [1]
    update_number(li2)
    print(li2)

The above will show:

* As value: ``[1]`` and ``[1]``, because in both cases, the list is copied by value (deeply), and that copy of the data is being changed.
* As reference: ``[2]`` and ``[2]``, because in both cases, there is a reference to the data being updated, not a copy of it.
* In most languages, where lists are behind pointers: ``[1]`` and ``[2]``. This is because in the first case, a new pointer is assigned, but to ``x``, which is just a copy of ``li1``, so it does not affect ``li1``. In the second case, ``x`` and ``li2`` are copies, but they point to the same data. It is the data being pointed to is changed, so ``li2`` is affected.

Note that these differences show up for mutable data that has more than one reference to it.

Pros and cons
-------------------------

The vast majority of languages copy data when passing (by value). But to varying degrees, they put things behind pointers (everything in Python, non-primitives in Java, or explicitly heap-allocated things in C).

Advantages of passing data directly by copying:

* You're confident a function won't re-assign your variable.
* You do not need to worry how long the referenced data is going to be alive.
* It can prevent heap allocations and associated cleanup, which are expensive.
* It's very fast, for small data.

Advantages of passing a reference to data:

* Functions can change arguments passed in (more powerful).
* The (maximum) size does not need to be known at compile time.
* No need to copy large objects.
* Potentially smaller code size with generics.

Everything by reference in Mango
-----------------------------------

In Mango, **all variables behave as references**.

As noted above, most languages pass by value. And some advantages of that approach were listed in the previous section.

Why, then, does Mango pass by reference?

* All the advantages mentioned above.
* It is more consistent for ``x = [1]`` and ``x[0] = 1`` to affect the outer scope in the same way.
* The disadvantages are mitigated by Mango's other features:

  * Complexity due to mutable parameters is less due to mutability being an explicit, opt-in choice.
  * A substantial part of the speed for small objects can oftentimes still be achieved by the compiler.
  * Data being pointed at cannot disappear in Mango. Data has a single owner, and only (s)he can move it. It gets deleted automatically at the end of its life.

.. note::
    Mango variables *behave* as reference. There is no guarantee that they will be implemented as references. The compiler may choose copy small variables if they are immutable or have a single owner, for example.

In short, by reference seems the more consistent choice for mutable parameters. The performance aspect is something for the compiler to worry about, and Mango's immutability and ownership help with that.

For many experienced programmers, passing by reference will be somewhat surprising. But many junior programmers will have been quite surprised in their early days by the mix of values and references in other languages.

A word of warning
---------------------------

While the idea is to help make mutability of arguments more consistent, please do not mistake this for an encouragement of updating arguments everywhere.

In many cases, the elegant solution is for parameters to be immutable input, and for the return value to be the only output. With opt-in mutability, Mango gives you the tools to work this way.
