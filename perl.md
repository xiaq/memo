`-l` is the symlink testing function.  eg::
 for my $f (glob '*') {
     if (! -l $f) {
         say $f;
     }
 }

`r` is the non-in-place substitution modifier.  eg::
 say $s =~ s/foo/bar/r;

`symlink` is equivalent to shell's ``ln -s``.
