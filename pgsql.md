A PostgreSQL instance manages a **database cluster**, which consists of some
**database**s, which in turn consist of **table**s.

# Commands

1. `postgres`: the daemon

1. `psql`: the shell

1. `createdb`, `dropdb`, `createuser`, `dropuser`: wrappers for SQL commands

# SELECT

`SELECT` is essentially "dump" and seems to be used for all kinds of
outputting:

    SELECT version();
    SELECT current_date;
    SELECT 1024 ^ 2;

Despite the usual rendering, SELECT seems to be case-*in*sensitive. More
saner examples:

    SELECT rolname from pg_roles; -- list all users on current cluster
    SELECT datname from pg_databases;

In `psql`:

    \?

# CREATE TABLE

Creating a table looks like:

    CREATE TABLE cities (
        name        varchar(80),
        location    point
    );

# INSERT

Inserting looks like:

    INSERT INTO cities VALUES ('Foo', '(3, 4)'); -- "positional"
    INSERT INTO cities (name, location) VALUES ('Foo', '(3, 4)') -- "keyword"

# More on SELECT

Filter with **WHERE** and **AND**:

    SELECT * FROM cities WHERE name = 'foo' AND name != 'bar';

Make up new fields on the fly with **AS**:

    SELECT location + '(1, 1)' FROM cities;

**ORDER BY**:

    SELECT * FROM cities ORDER BY name;

**DISTINCT**:

    SELECT DISTINCT name FROM cities;

## Join

By specifying multiple tables after FROM, you do a **join**.

    CREATE TABLE students (id int, name varchar(80));
    CREATE TABLE scores (id int, s1 int, s2 int);
    SELECT * FROM students, scores WHERE students.id = scores.id;

Which was an **inner join**. There are also **outer join**s, which mandate
each row of *some* table to appear at least once, even when not matched by
WHERE (fields from the *other* table are left empty). Depending on which table
is *some*, there are **left outer**, **right outer** and **full outer join**s:

    SELECT * FROM students LEFT OUTER JOIN scores ON students.id = scores.id;
    -- Similar for other types

NOTE: When doing joins explicitly, WHERE is replaced by ON.

Aliasing:

    SELECT * FROM students st, scores sc WHERE st.id = sc.id;

Besides abbreviating, aliasing is required to distinguish left and right side
of the join when doing a **self-join**:
