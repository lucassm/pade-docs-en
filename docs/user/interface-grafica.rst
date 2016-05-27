GUI
===

Activating the GUI in PADE is rather simple, as it is only necessary to set parameter gui=True in the following function:

::

    start_loop(agentes, gui=True)

PADE GUI is currently simple and does not present many functions, since its implementation is based on framework Qt/PySide, thus bringing some complex issues to be solved. However, version 2.0 is supposed to present a more complete and functional web-based GUI using `Flask <http://flask.pocoo.org/>`_ framework.
