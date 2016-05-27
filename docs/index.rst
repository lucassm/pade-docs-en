.. Pade documentation master file, created by
   sphinx-quickstart on Sat Sep 12 19:30:28 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Python Agent DEvelopment framework
==================================

Multi-Agent Systems in Python!
------------------------------

PADE is a framework for the development, execution, and management of multi-agent systems in distributed computer environments.

PADE is fully written in Python code and uses the libraries from `Twisted <http://twistedmatrix.com/>`_ project to allow communication amonge the network nodes.

PADE is freeware, licensed under the MIT license terms, developed by the Smart Power Grids Research Group (GREI) with the Department of Electrical Engineering of the Federal University of Ceará.

Anyone who is interested to contribute to the project is invited to download, run, test, and provide the developers with feedback about the platform.

PADE is Simple!
~~~~~~~~~~~~~~~~~

::

    # This is file start_mas.py
    from pade.misc.common import set_ams, start_loop

    if __name__ == '__main__':
        set_ams('localhost', 8000)
        start_loop(list(), gui=True)


PADE is easy to install!
~~~~~~~~~~~~~~~~~~~~

To install PADE, just type the following command line from the prompt in a Linux terminal:

::

    $ pip install pade
    $ python start_ams.py

General Functionalities
~~~~~~~~~~~~~~~~~~~~~~~

PADE was developed according to requirements for automation systems. It offers the following library resources for the development of multi-agent systems:


**Object Orientation**
  abstraction for the implementation of a proper environment that allows agents to be executed using object-oriented concepts;

**Execution Environment**
  module for the initialization of the agent execution environment, which is entirely developed in Python code;

**FIPA-ACL standard messages**
  module for the implementation and handling of FIPA-ACL messages;

**Message Filter**
  module that allows filtering messages as desired;

**FIPA Protocols**
  module for the proper implementation of protocols as defined by FIPA;

**Cyclic and Temporal Behaviors**
  module for the implementation of cyclical and temporal behavior;

**Database**
  module for the interaction with database;

**Sending Serialized Objects**
  it is possible to send serialized objects as a content of FIPA-ACL messages.


In addition to the aforementioned functionalities, PADE is easy to install and setup, being multi-platform so that it can be installed and used in embedded hardware running distinct operating systems such as Linux, Raspberry Pi, BeagleBone Black, as well as Windows.


User Guide
----------

.. toctree::
   :maxdepth: 2

   user/instalacao.rst
   user/hello-world
   user/meu-primeiro-agente
   user/agentes-temporais
   user/enviando-mensagens
   user/recebendo-mensagens
   user/um-momento
   user/enviando-objetos
   user/selecao-de-mensagens
   user/interface-grafica
   user/protocolos



PADE API References
-------------------

.. toctree::
   :maxdepth: 2

   api


