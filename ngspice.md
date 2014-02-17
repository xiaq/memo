Syntax and structure of source code
===================================

1. Spice is case-insensitive.

1. The first line of source is the title and the only comment line that needs
   no special character; the last line must be ``.end``. The lines between
   them are known as `element lines`.

1. Lines starting with ``+`` continues the previous line.

1. Lines starting with ``*`` are comments; Any of ``;``, ``$ `` (dollar and
   space), ``//`` or ``--`` introduces inline comments. (ng-spice)

1. An element line consist of several `fields`: the `name`, the `circuit
   nodes` to which it is connected, and the `values of parameters`
   charactering the element. The type of the element is determined by *the
   first letter of the name*.  Blanks, commas, ``=`` and paratheses separate
   tokens; extra blanks are ignored.

1. `Node names` are arbitary strings. They are treated literally, not
   evaluated as numbers; so ``00`` and ``0`` are different. There is one
   preset node, ``0`` (the ground). ``gnd`` is an alias for it.

1. Nodes are created implicitly, ie. when they first occur on an element line;
   except the preset ``0``, which also must be present in any circuit.

1. `Numbers` may be integers or floating numbers. Floating numbers may be
   expressed in the conventional scientific notion, like ``1.2e34``. SI
   suffixes are understood in the following forms: Tera, G, Meg, K, m, u, n,
   p, f. A non-SI suffix "mil" is also accepted, standing for 2.54e-5.

1. Any characters not recognized as suffixes are ignored, so that ``10V``,
   ``10Volts`` are the same as ``10``. Spice doesn't need to know the units;
   since paramters have fixed positions, they are assigned automatically.

Basic Directives
================

1. ``.title``: the title. This is implicit for the first line.

1. ``.end``: the end.

1. ``.model <name> <type> (<pname1>=<pval1> ...)

