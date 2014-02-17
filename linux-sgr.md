*Color escape code* s take the form of:

	^[[??m

^[ is the charracter ESC and may be written as \e or \033. Examples:

	^[[01m
	^[[1m (preceeding 0's may be omitted)

	^[[0m
	^[[m (0 alone may be omitted)
	
	^[[1;7m (multiple codes may be put together)

Terminology
===========
*Normal* colors are 3-bit clear ones; *intensive* colors, in contrary, are the ones with 3-bit set, usually brighter than their normal counterparts.

Legend
======
"rx" is tmux within roxterm; "lx" is tmux in Linux console

Codes
=====
Styles
------
01 bold/bright: intensive fg, bold font (rx)
              : intensive fg (lx)
02 faint/dim  : no effect (rx)
              : fg always #6 (which is normal cyan)
03 standout   : same as reverse (rx, lx)
04 underline  : underline, line color fg; bg untouched (rx)
              : same as faint (lx)
05 blink      : no effect (rx)
              : intensive bg color (lx)
06 (missing)
07 reverse    : fg and bg colors swap (rx, lx)
08 conceal    : text replaced by white space (rx)
              : no effect (lx)

note: 7;1 or 1;7 both give intensive bg (which is original fg).

Clearing styles
---------------
00 none       : clear all styles and colors
21 (missing)
22 normal     : clear bold and faint
(for v = 23...27, v corresponding to v-20)
23 no-standout
24 no-underline
25 no-blink
26 (missing)
27 no-reverse

Colors
------
30 ~ 37: foreground: black, red, green, yellow, blue, magenta, cyan, white
40 ~ 47: background: (same)

Reference
=========
man 4 console_codes

