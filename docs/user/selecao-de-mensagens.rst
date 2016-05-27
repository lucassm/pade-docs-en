Filtering Messages
==================

It is possible to implement message filters in PADE in a simple and direct way using class *Filter()*:

::

    from pade.acl.filters import Filter

Filtering messages with Filters module
--------------------------------------

Let’s consider the following message:

::

    from pade.acl.messages import ACLMessage
    from pade.acl.aid import AID

    message = ACLMessage(ACLMessage.INFORM)
    message.set_protocol(ACLMessage.FIPA_REQUEST_PROTOCOL)
    message.set_sender(AID('remetente'))
    message.add_receiver(AID('destinatario'))


In this case, it is possible to create the following filter:

::

    from pade.acl.filters import Filter

    f.performative = ACLMessage.REQUEST


It is possible to notice how the filter works when applied to a message in a Python interpreter session.

.. code-block:: python

    >> f.filter(message)
    False


Now, the filter is adjusted for another condition:

.. code-block:: python

    f.performative = ACLMessage.INFORM

Once again, it is applied to the message, as a new result is obtained.

.. code-block:: python

    >> f.filter(message)
    True
     
