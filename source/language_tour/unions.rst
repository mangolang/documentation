
Union
===============================

Similar to / also known as: sum type, enum, enumeration, oneof.

One of
-------------------------------

It is possible to specify that *one of* several types should be used.

.. code-block::

	record Network:
         socket: Socket
         secure: Boolean
	record Disk:
		fh: FileReadHandle

	union DataSource = Network | Disk

In this case, the ``DataSource`` is either a network or a disk instance.

This could also be achieved by doing:

.. code-block::

	union DataSource:
		record Network:
            socket: Socket
            secure: Boolean
        record Disk:
			fh: FileReadHandle

The only difference is that ``Network`` and ``Disk`` are inside the namespace ``DataSource``.

Unless explicitly implemented, unions automatically implement those trait that are implemented by every variant, by delegating to the current variant.

Tagged vs untagged
-------------------------------

There are some differences between these 'one of' types in different languages. Many languages have nothing, or only have enums that cannot hold instance data.

Of languages that have more expressive sum union types, there are two variants:

* Tagged (sum types): each variant has a name and so can be distinguished, even if the types or values are the same. E.g. the type would not be ``String | int | int``, but rather ``A(String) | B(int) | C(int)``.
* Untagged (union types): possible values are all values of member types, with duplicates removes. So ``String | int | int`` is the same as ``String | int``, as the two integer variants are indistinguishable.

**Mango uses untagged unions**.

.. note::
    Note that by 'untagged' it is not meant the language does not know which variant is present. So Mango is not like C. It merely means no explicit name is used to tag types.

You can create your own tags easily, and you are usually encouraged to do so:

.. code-block::

	union Tagged:
		record A(String)
		record B(int)
		record C(int)

Unions vs trait impl
-------------------------------

This has some parallels to inheritance, or to implementing traits.

The variants ``A``, ``B`` and ``C`` of ``union U = A | B | B`` are assignable to variables of type ``U``, and nothing else is.

The same would be true if ``U`` were a trait and ``A``, ``B``, and ``C`` the record implementing it.

Indeed, languages like Kotlin implement sum types as a special form of inheritance (using ``sealed``). In Mango the parallel is less explicit.

The biggest difference with between union variants and trait implementations, is that union variants form a _closed_ group: all members are known and fixed.

This has the result that downcasting only makes sense for unions, not for traits (there are technical reasons as well). Downcasting a trait to a specific record would mean that that record is treated differently from any other implementation of the trait. This is an odd choice to make if you can't know which implementations there are (because anyone could have created one).

Another difference in some languages, is that a record can implement any number of traits, but a variant can only belong to one union. This is _not_ the case in Mango, a record can belong to multiple unions:

.. code-block::

	record A
	record B
	record C
	union P = A | B
	union Q = B | C

Notes
-------------------------------

* While there are expressive ways to require combinations of types, there is no general way to require the _absense_ of a type (i.e. no way to make sure that a trait is not implemented for a record or union).
* With product types (records) and sum types (unions), Mango has algebraic types.
