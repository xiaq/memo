`cgitb` is a traceback helper module. (`tb` for traceback.) What the hell does it have to do with cgi then? Turns out it is intended to be used to show traceback info for web applications in the browser... which is not mentioned in the docstring.

To embed IPython, just do::

  from IPython import embed
  embed()
