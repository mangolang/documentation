
Records
====================================

Similar to / also known as: class, struct, product type.

Records
-------------------------------

Like most languages, Mango lets you combine several individual fields into a single type:

.. code-block::

	record Person:
		name: Name,
		birthday: PastDate

You can then create a ``Person`` instance using

.. code-block::

	let her = Person(
		name = Name::new("Eve").unwrap(),
		birthday = PastDate::new(1988, 1, 31),
	)

Record types can have behaviour associated with them, mostly using traits, but also directly:

.. code-block::

	impl Person:
		fn greet(&self):
			print("hello, 0:s", self.name)

In the future, Mango might support an 'anonymous' version of records, where no record name or member names need to be specified. (This is like tuples in some languages).

No inheritance
-------------------------------

Records in Mango cannot extend other records. There is no inheritance of fields or logic.

There is polymorphism, however. A record can implement a trait, and different implementations of the trait can then be used polymorphically. That is, you can write code for ``Fruit``, and it can be used for ``Apple`` and ``Orange``. Virtual calls are also supported.

How does Mango solve the problems that Java solves with inheritance?

* Behaviour can be shared by delegating.
* Runtime polymorphism is possible using traits with ``#``.

Why not just inheritance or behaviour and data? This is too big a topic to do justice, but briefly:

* It creates tight coupling between the super and subclass. Especially the inability to change the superclass because anyone might have relied on any of it is harmful (fragile base class).
* It is easy while debugging to be surprised by an overload being called instead of method on the reference type.
* Code-sharing and polymorphic abstraction are separate concepts. If they are conflated, it is easy to end up with subclasses that can't really replace their parent, they just shared some logic.

It is also not possible to embed the fields of a record inside another record, as in Go. You can of course have a record field that is another record.

There is currently no special syntax for delegation, to mimic inheritance. Delegation is encouraged though, so it is not impossible that such syntax will one day be added.
