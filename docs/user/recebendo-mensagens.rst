Receiving messages
==================

In order to allow agents to receive messages in PADE, it is simply necessary to implement `react()` method inside the class that inherits information from class `Agent()`.

Receiving FIPA-ACL messages in PADE
-----------------------------------

The following example shows the implementation of two distinct agents: ```sender```, which is modeled by class `Sender()`, being responsible for sending a message; and `receiver`, which is modeled by class `Receiver()`, which receives the sent message and also aggregates `react()` method.

::

    from pade.misc.utility import display_message
    from pade.misc.common import set_ams, start_loop
    from pade.core.agent import Agent
    from pade.acl.aid import AID
    from pade.acl.messages import ACLMessage


    class Remetente(Agent):
        def __init__(self, aid):
            super(Remetente, self).__init__(aid=aid, debug=False)

        def on_start(self):
            display_message(self.aid.localname, 'Enviando Mensagem')
            message = ACLMessage(ACLMessage.INFORM)
            message.add_receiver(AID('destinatario'))
            message.set_content('Ola')
            self.send(message)

        def react(self, message):
            pass


    class Destinatario(Agent):
        def __init__(self, aid):
            super(Destinatario, self).__init__(aid=aid, debug=False)

        def react(self, message):
            display_message(self.aid.localname, 'Mensagem recebida')


    if __name__ == '__main__':

        set_ams('localhost', 8000, debug=False)

        agentes = list()

        destinatario = Destinatario(AID(name='destinatario'))
        destinatario.ams = {'name': 'localhost', 'port': 8000}
        agentes.append(destinatario)

        remetente = Remetente(AID(name='remetente'))
        remetente.ams = {'name': 'localhost', 'port': 8000}
        agentes.append(remetente)

        start_loop(agentes, gui=True)


GUI
---

It is possible to see PADE GUI as follows, which shows the agents registered in the multi-agent system.

.. figure:: ../img/janela_agentes.png
    :align: center
    :width: 4.5in

By clicking the message received by the agent, it is possible to see its respective content.

.. figure:: ../img/janela_mensagem.png
    :align: center
    :width: 3.0in