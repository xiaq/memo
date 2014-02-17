# Structure of .git

Reference: http://progit.org/book/ch9-1.html

* branch: not used by newer versions of Git

* description: used by GitWeb

* hooks: hooks ;-)

* HEAD: *DontKnowYet*

* config: repo-wise configuration

* objects: The Git Object Store

* refs:

# Plumbing commands

* `git hash-object < $filename | --stdin >`: get hash of object; with `-w`,
  write to object store

* `git cat-file <>`
