
Traits (interfaces)
===============================

.. todo: traits


Intersection types
-------------------------------

It is also possible to specify a combination of types, if the types are traits:

.. code-block::

	fn pythagoras(x: T, y: T) -> T where T = Add<T, Out=T> & Mul<T, Out=T>:
        x * x + y * y

Here ``T`` is a type that implements both ``Add`` and ``Mul``.

Intersection types are not distinct concrete types (like records or unions), just bound on existing concrete types. You cannot create an instance of ``Add & Mul``, but it is nonetheless very useful for type parameters.

Note that it does not make sense to create an intersection containing one or more known, concrete types.

* Two concrete types does not make sense because an object cannot have two concrete types.
* One concrete type with a trait does not make sense because a concrete type already implies a known set of traits per scope, so it is either always or never satisfied.
