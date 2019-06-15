
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
* ``in``: In combination with ``if`` or ``for``.
* ``fun``: Declares a function.
* ``return``: (Early) return from a function (hint: may be omitted for final return).
* ``and``: Boolean 'and'.
* ``or``: Boolean 'or'.
* ``not``: Boolean 'not'.

This list is sure to grow.

Symbols
-------------------------------

``%`` (percentage)
  Comment.

``%%`` (double percentage)
  Documentation.

``:`` (colon)
  After a value, this is followed by a type tag.

  In combination with various keywords, this starts a block, either multiline by indentation, or inline.

``+``, ``-``, ``*``, ``/`` (plus, minus, asterisk, slash)
  As binary operators, these are the usual mathematical operations.

  As unary operators, ``+`` and ``-`` are positive and negative values.

  In types, ``X*`` is a shorthand for a collection of ``X``.

``//`` (double slash)
  As binary operator, integer division.

``==``, ``>``, ``<``, ``<=``, ``>=``
  Ordering operators.

``=`` (single equals)
  Assignment, parameter default, named arguments, map literals.

``+=`` (operator and equals)
  Updating assignment (note ``a += b`` can be a different operation from ``a = a + b``).

``"string"`` (double quotes)
  String literal.

  Note that single quotes cannot be used for strings.

``x"string"`` (letter followed by string)
  Modified string literal, e.g. raw or templated.

``[1, 2]`` (square brackets)
  As a value, this is an array literal.

  As a postfix for a value, this is indexing.

  As a postfix for a type, this is a generic parameter.

``{a=2}`` (curly braces)
  Map literal.

``()`` (parentheses)
  Used for grouping, function invocation, used in function signatures.

newline
  End of statement unless following ellipsis.

``...`` (ellipsis)
  At the end of a line, this means the next line is a continuation of the same statement.

``,`` (comma)
  Separator in array or map literals and in function signatures of calls.

  A comma is optional if it would be at the end of a line.

``.`` (period)
  Access a method or field

``?`` (question mark)
  As a postfix for a value, this unwraps a result type, returning early in case of failure.

  In types, ``X?`` is a shorthand for an optional of ``X``.

``&`` (ampersand)
  As a prefix for values or types, this indicates borrowing.

  .. warning::
      Ampersand might change to postfix.

``#`` (hash)
  As a type prefix, ``#X`` means a dynamic, mixed types implementing ``X`` (whereas ``X`` is a a static, pure type implementing ``X``). See :doc:`/language_tour/type_parameters`

  .. warning::
      Hash might change to postfix.

``|`` (pipe)
  For values, apply an operation to every element in a collection.

  .. warning::
      Pipe is not confirmed yet.

``@`` (at)
  As a value postfix, this awaits the result.


Note that these symbols, common in several languages, do not have their C-like meaning in Mango:

* ``x++`` and ``x--``: use ``x += 1`` or ``x -= 1``
* ``&&`` and ``||``: use ``and`` or ``or``

TODO: Several symbols in Mango have a double meaning: one in a type and one in a value.

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
