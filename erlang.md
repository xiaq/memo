Like in Prolog, *statement*s end with periods:

    1 > 2.

Like in Prolog, *variable*s start with upper case:

    A = 2.

Unlike in Prolog, `=` is the binding operator, not unification predicate.
Binding cannot be altered, the following causes error:

    A = 2.
    A = 3.

Like in Prolog, `_` is the dummy variable and can is always free:

    _ = 2.
    _ = 3.

Variables can be erased with `f()` _in a shell_:

    A = 2.
    f(A).
    A = 3.

Like in Prolog, *atom*s either start with lower case or is enclosed in single
quotes:

    atom.
    'Atom'.
    '~!@#$%^&*()'.

Comparison operators:

    ==      like JavaScript "=="
    /=      like JavaScript "!="
    =:=     like Javascript "==="
    =/=     like Javascript "!=="
    >
    >=
    <
    =<

*Tuple*s:

    Point = {3,4}
    {X,Y} = Point
    {X,_} = Point

*List*s (heterogeneous):

    [1, {x}].
    "你好" = [20320, 22909].

List builtins:

    hd([1,2,3]).
    tl([1,2,3]).
    length([1,2,3]).
