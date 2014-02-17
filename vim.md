# Keybinding

``g]``
    Like Ctrl-], but list candidates

# Defining User Commands

* Names must start with a capital letter.

* Arguments: ``:command -nargs=+ Say :echo "<args>"``

  * -nargs= follwed by number of arguments. Possible values: \d+, ``*``,
    ``?``, ``+``.  Meanings are similar to those in regexp.

  * Arguments are represented by ``<args>`` keyword.  Possible Variations to
    ``<args>`` are ``<q-args>`` (quoted) and ``<f-args>`` (expands to an
    function call argument list).

* Other options to ``:command`` may be useful.

* Use ``<lt>`` keyword to insert a ``<``.

# Tags

* tj[ump] [tag]: jump to tag or display a list of tags when there is more than one.

* stj[ump]: split and :tjump.
