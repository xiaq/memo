Function definitions are written like appliance:

    norm a b = sqrt(a^2 + b^2)

Local bindings are written with `where` in suffix order:

    heron a b c = sqrt(s * (s-a) * (s-b) * (s-c)) where s = (a + b + c) / 2

    heron a b c = result where result = sqrt(s * (s-a) * (s-b) * (s-c))
                               s = (a + b + c) / 2

`==` operates only on values with same type, otherwise it throws an exception:

    1 == True

Infix operators can be referred to by enclosing in parenthesis:

    (>) "A" "a"

Relation operators roundup:

    &&    and
    ||    or
    not   not
    /=    not equal

Guards are written like:

    abs x
        | x < 0 = -x
        | otherwise = x

Destructing:

    myhead [x:xs] = x

Pattern matching:
