
.. warning::
    The syntax is not complete yet, this will likely be expanded before Mango 1.0.

Keywords
===============================

Keywords
-------------------------------

* ``import``: At the top of a source file, import another file or package.
* ``record``: See :doc:`/language_tour/records`.
* ``union``: See :doc:`/language_tour/unions`.
* ``trait``: See :doc:`/language_tour/traits`.
* ``let``: Declares a variable.
* ``mut``: Makes a reference mutable.
* ``if``: A condition.
* ``else``: In combination with ``if``, the alternative case.
* ``for``: A for-loop that iterates over an iterator.
* ``while``: A while-loop that iterations until a condition no longer holds.
* ``fun``: Declares a function.
* ``return``: (Early) return from a function (hint: may be omitted for final return).
* ``and``: Boolean 'and'.
* ``or``: Boolean 'or'.
* ``not``: Boolean 'not'.

This list is sure to grow.

Symbols
-------------------------------

These are general syntax symbols:

``%`` (percentage)
  Comment

``%%`` (double percentage)
  Documentation

``...`` (ellipsis)
  A line continuation

``:`` (colon)
  After a value, this is followed by a type tag.

  In combination with various keywords, this starts a block, either multiline by indentation, or inline.

``=`` (single equals)
  Assignment, parameter default, named arguments, map literals

``+``, ``-``, ``*``, ``/`` (plus, minus, asterisk, slash)
  Mathematical operations

  (note that ``*`` has another meaning in types)

``//`` (double slash)
  Integer division

``+=`` (operator and equals)
  Updating assignment (note ``a += b`` can be a different operation from ``a = a + b``)




Several symbols in Mango have a double meaning: one in a type and one in a value.



Reserved
-------------------------------

Adding a keyword is a breaking change, so a large number of keywords are currently marked as reserved. Some of them will probably be released before Mango 1.0.

* ``abstract``
* ``alias``
* ``all``
* ``annotation``
* ``any``
* ``as``
* ``assert``
* ``async``
* ``await``
* ``become``
* ``bool``
* ``box``
* ``break``
* ``by``
* ``byte``
* ``catch``
* ``class``
* ``closed``
* ``companion``
* ``const``
* ``constructor``
* ``continue``
* ``data``
* ``debug``
* ``def``
* ``default``
* ``defer``
* ``del``
* ``delegate``
* ``delegates``
* ``delete``
* ``derive``
* ``deriving``
* ``do``
* ``double``
* ``dynamic``
* ``elementwise``
* ``elif``
* ``end``
* ``enum``
* ``eval``
* ``except``
* ``extends``
* ``extern``
* ``false``
* ``family``
* ``field``
* ``final``
* ``finally``
* ``float``
* ``fn``
* ``get``
* ``global``
* ``goto``
* ``impl``
* ``implements``
* ``in``
* ``init``
* ``int``
* ``interface``
* ``internal``
* ``intersect``
* ``intersection``
* ``is``
* ``it``
* ``lambda``
* ``lateinit``
* ``lazy``
* ``local``
* ``loop``
* ``macro``
* ``match``
* ``module``
* ``move``
* ``NaN``
* ``native``
* ``new``
* ``nill``
* ``none``
* ``null``
* ``object``
* ``open``
* ``operator``
* ``out``
* ``override``
* ``package``
* ``param``
* ``pass``
* ``private``
* ``public``
* ``pure``
* ``raise``
* ``real``
* ``rec``
* ``reified``
* ``sealed``
* ``select``
* ``self``
* ``set``
* ``sizeof``
* ``static``
* ``struct``
* ``super``
* ``switch``
* ``sync``
* ``synchronized``
* ``tailrec``
* ``this``
* ``throw``
* ``throws``
* ``to``
* ``transient``
* ``true``
* ``try``
* ``type``
* ``unite``
* ``unsafe``
* ``until``
* ``use``
* ``val``
* ``var``
* ``vararg``
* ``virtual``
* ``volatile``
* ``when``
* ``where``
* ``with``
* ``xor``
* ``yield``
