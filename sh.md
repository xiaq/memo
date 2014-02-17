# POSIX

Two ways of grouping commands:

    (list) # spawns a subshell
    { list; } # doesn't spawn subshell

"}" is a reserved word and thus must appear at beginning of a line of after a
control character, like "then" and "do". ")" is magical.

`source` is not supported by dash. Always use `.`.

`\a` outside any quote is always plainly "a"

Redirect stderr:
    COMMAND 2> FILE

# UNIX-y utilities

    grep
    # context control:
        -A # after context
        -B # before context
        -C # context; lines around matches
    -n # line number
    -v # invert match; lines that don't match. Misleading enough...
    -l # list files that match

    cat -A # show all charactors (esp. control characters, using ^ and M- notations)

    file -s # Force statting special file

    less -r # Put raw characters directly to output, instead of converting to "^A", etc. Useful when displaying colored output

Usage of Linux getopt:
    eval set -- "$(getopt -s sh -o abc: -- "$@")"

# bash

(May also apply to zsh)

    'ls' # avoid aliases

# zsh

## Keybinding

`M-x`: execute zle command

`M-_` or `M-.`: insert last word of last command

## Syntax constructs

`<<<`: here string
