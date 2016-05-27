Sending objects
===============

It is not always possible to represent the content that must be sent to other agents using a simple text, is it?

In order to attach objects to FIPA-ACL messages in PADE, it is only necessary to use the Python native module called *pickle*.

Sending serialized objects using pickle
---------------------------------------

The following steps can be used to send a serialized object with pickle:

::

    import pickle

*Pickle* is a library dedicated to serialized objects, while `pickle.dumps()` must be used according to the following syntax:

::

    dados = {'nome' : 'agente_consumidor', 'porta' : 2004}
    dados_serial = pickle.dumps(dados)
    message.set_content(dados_serial)

Done! The object can now be sent as attached to the message content.

Receiving serialized objects using pickle
-----------------------------------------

Now, the object can be received by loading it with the following command:

::

    dados_serial = message.content
    dados = pickle.loads(dados_serial)

Plain simple ;)