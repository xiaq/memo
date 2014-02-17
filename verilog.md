Delays add up, even with non-blocking assignments.

To generate multiple clocked signals, use multiple `always` blocks::

    always
        #1 clk <= !clk;
    always
        #2 a <= !a;

