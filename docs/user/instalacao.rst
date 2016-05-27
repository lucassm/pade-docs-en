Installation
==========

Installing PADE in your PC, laptop, or embedded device is quite easy. You just need to be connected to the internet!

Installation via pip
--------------------

To install PADE via pip, just type the following command line:

.. code-block:: console

    $ pip install pade


Done! PADE is installed!

.. warning::
    Warning: PADE has been officially tested in Ubuntu 14.04 LTS environment, as it is necessary to install packages python-twisted-qt4reactor and pyside for this purpose.

Installation via GitHub
-----------------------

If you wish to access PADE source code and install it using this approach, just type the following command lines:

.. code-block:: console

    $ git clone https://github.com/lucassm/Pade
    $ cd Pade
    $ python setup.py install 

Done! PADE is ready to be used! Test Python interpreted using the following command:

::

    from pade.misc.utility import display_message

Installing PADE in a virtual environment
----------------------------------------

When dealing with Python modules, it is important to know how to create and manipulate virtual environments in order to manage the project dependencies in a more organized way. Here we will show how it is possible to create a virtual Python environment, activating it and using pip to install PADE. Please, access `Python Guide <http://docs.python-guide.org/en/latest/dev/virtualenvs/>`_ for a more detailed view on virtual Python environments:

Firstly you need to install virtualenv package in your PC typing the following command:

.. code-block:: console

	$ pip install virtualenv

After installing virtualenv, it is time to create a virtual environment with the following command:

.. code-block:: console
	
	$ cd my_project_folder 
	$ virtualenv venv

Type the following command to activate the virtual environment:

.. code-block:: console
	
	$ source venv/bin/activate

Now, just install PADE via pip:

.. code-block:: console

	$ pip install pade
 

Activating the graphical user interface (GUI)
---------------------------------------------
 
It is necessary to install PySide package, which is a Qt binding, so that PADE graphical user interface (GUI can be properly used. Since there are no Pyside binaries available for Linux and the involved procedure is quite long, it is necessary to perform the following actions:

1. Install PySide with the following command:

.. code-block:: console

	$ sudo apt-get install python-pyside

2. Copy PySide installation folder from folder site-packages, which is the standard path used by your operating system, to the one where the standard packages of the virtual environment are currently installed. In this case, the path is venv/lib/python2.7/site-packages.

Done! PySide is installed in the virtual environment, but another procedure must still be carried out, which consists in installing the reactor that interacts with Pyside event loop. For this purpose, type the following command:

.. code-block:: console

	$ sudo apt-get install python-qt4reactor

