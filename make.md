This memo applies to GNU Make.

Write wildcard rules like:
    %: %.c

Automatic variables:

* `$@` target
* `$<` first prerequisite
* `$*` the stem in a wildcard rule
* `$+` all prerequisites
* `$^` all prerequisites, removing duplicates

Functions:

* `$(wildcard PATTERN)`
* `$(subst FROM,TO,TEXT)`
* `$(patsubst PATTERN,REPLACEMENT,TEXT)` `%` serves as wildcard as in
  wildcard rules.
* `$(VAR:SUFFIX=REPLACEMENT)` is equivalent to
  `$(patsubst %SUFFIX, %REPLACEMENT, $(VAR)` provided SUFFIX contains no %.
