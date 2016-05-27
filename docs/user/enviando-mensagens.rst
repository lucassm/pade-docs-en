Sending messages
================

Sending a message using PADE is quite simple! The messages sent by PADE-based agents use FIPA-ACL standard and have the following fields:

* *conversation-id:* conversation unique identity;
* *performative:* message label;
* *sender:* message sender;
* *receivers:* message receivers;
* *content:* message content;
* *protocol:* message protocol;
* *language:* adopted language;
* *encoding:* encoding message;
* *ontology:* adopted ontology;
* *reply-with:* expression used by the answer agent to identify a message;
* *reply-by:* reference to a previous action, where the message is an answer.
* *in-reply-to:* date/time label indicating when an answer must be received.

FIPA-ACL messages in PADE
-------------------------

A FIPA-ACL message can be structured in the following form: 

::

    from pade.acl.messages import ACLMessage, AID
    message = ACLMessage(ACLMessage.INFORM)
    message.set_protocol(ACLMessage.FIPA_REQUEST_PROTOCOL)
    message.add_receiver(AID('agent_receiver'))
    message.set_content('Hello, Agent!')


Sending a Message in PADE
-------------------------

Once inside a given instance of class Agent(), the message can be sent by simply typing the following command:

::

    self.send(message)


FIPA-ACL standard messages
--------------------------

By using print message command, a FIPA-ACL message will be displayed as follows:

::

    (inform
        :conversationID b2e806b8-50a0-11e5-b3b6-e8b1fc5c3cdf
        :receiver
            (set
                (agent-identifier
                    :name agent_destination@localhost:51645
                    :addresses 
                        (sequence
                        localhost:51645
                        )
                )

            )
        :content "Hello, agent!"
        :protocol fipa-request protocol
    )


XML standard messages
---------------------

It is also possible to get messages in XML format using `print message.as_xml()` command.

.. code-block:: xml

    <?xml version="1.0" ?>
    <ACLMessage date="01/09/2015 as 08:58:03:113891">
            <performative>inform</performative>
            <sender/>
            <receivers>
                    <receiver>agente_destino@localhost:51645</receiver>
            </receivers>
            <reply-to/>
            <content>Ola Agente</content>
            <language/>
            <enconding/>
            <ontology/>
            <protocol>fipa-request protocol</protocol>
            <conversationID>b2e806b8-50a0-11e5-b3b6-e8b1fc5c3cdf</conversationID>
            <reply-with/>
            <in-reply-to/>
            <reply-by/>
    </ACLMessage>
