Basics
======

* `Atoms` are either

  - Words starting with lower-case

  - Words enclosed by single quotes

  - Strings of special character, like ``:-``, ``=``. Some of these have
    predefined meanings.

* `Variables` start with upper-case

* **:-** "if"; `rule` constructor

  - **;** "or"
  - **,** "and"

* **?-** `question` constructor

* ``consult '/path/to/source.pl'.`` or
  ``['/path/to/source.pl'].`` to load a source

*  ``listing.`` or ``listing(predicate).`` to inspect

* `Comments` start with ``%``

Unification
===========

* Predicate notion: `predicate/n`, like `=/2`

* Both prefix and infix notions are available for `=` (unify) predicate

* Terms may be constructed out of thin air in `.pl` sources, but not in
  queries

* Unification: possible identicalness.

  - Atoms unify when they are equal

  - Variables may unify with anything else

  - Complex terms unify recursively

  - Infinite loop (on a poor Prolog implementation)::

      ?- X = parent(X).

  - "Defensive" unification ``unify_with_occurs_check/2``::

      ?- unify_with_occurs_check(X, parent(X)

  - Unification is done through search and backtrack

    + Orders of rules matter

    + How is complex term unification possible then? Question remains.

Lists
=====

* Lists are heterogenous and denoted like::

    ?- X = [ 1, 2, [], Y, ala ].

  Notice the different semantics of commas here.

* ``|`` is the list decomposition operator::

    ?- [Head|Tail] = [ 1, 2, [], Y, ala ].
    Head = 1,
    Tail = [2, [], Y, ala].

    ?- [First,Second|Tail] = [ 1, 2, [], Y, ala ].
    First = 1,
    Second = 2,
    Tail = [[], Y, ala].

* Dummy variable ``_`` - "discard it"::

    ?- [Head,_,_|Tail] = [ 1, 2, [], Y, ala ].
    Head = 1,
    Tail = [Y, ala].

  Multiple occurences of ``_`` need not unify.

* Builtin ``member`` predicate is defined as follows::

    member(X, [X|T]).
    member(X, [_|T]) :- member(X, T).

Arithmetics
===========

* ``is/2`` predicate::

    ?- X is 1+2.
    X = 3.

    ?- is(X, 1+2).
    X = 3.

  Equations should be on the right hand side.

* Arithmetic operators ``+ - * / and mod`` are just atoms. As predicates they
  can be used in prefix notion too (rather Scheme-like)::
  
    ?- is(X, +(1, 2)).
    X = 3.

Grammars
========

* Language processing is one of Prolog's initial missions; CFG can be
  constructed directly using ``append/3``

* Due to inefficiency of ``append/3``, the `difference list` technique is
  employed.
  
* Prolog provides sugar for the above technique, denoted using the ``-->``
  operator and written like a ordinary CFG::

    s --> np, vp
    % Equivalent to:
    s(X, Y) :- np(X, Z), vp(Z, Y).

