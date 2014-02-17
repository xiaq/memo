Tracing the way to templating
=============================

roundup_server.py: run() -> `class ServerConfig` .get_server() ->

BaseHTTPServer.py: `class HTTPServer` .serve_forever() -> 

roundup_server.py: `class RoundupRequestHandler`: .run_cgi() -> .inner_run_cgi() -> .get_tracker()

instance.py: `class Tracker`: .Client.main() ->

cgi/client.py: `class Client` .main() -> .inner_main() -> .renderContext() ->

instance.py: `class Tracker`: .templates.get() ->

cgi/templating.py: `class Templates`: .get() -> `class RoundupPageTemplate`: .render() ->

- cgi/TAL/TALInterpreter: `class TALInterpreter`: .__call__()

- (for context passing) cgi/PageTemplates/Expressions.py: getEngine() ->
  cgi/PageTemplates/TALES.py: `class Engine`: getContext() -> `class Context`

Mixing in the context
---------------------

cgi/templating.py: context() creates an instance of `client.instance.interfaces.TemplatingUtils` (falling back on default TemplatingUtils) and assigns it to the context variable `utils`.

instance.py: Upon init `Tracker` executes (``execfile``) file `interfaces.py` in tracker home. `interfaces.py` may define classes `Client` (inheriting from roundup.cgi.client.Client) and `MailGW` (from roundup.mailgw.MailGW), which will be loaded by the `Tracker` instance.

The Tracker instance's `self.interfaces` is *NOT* set. This is likely to be a bug.
