 One moment, please!
====================

PADE allows postponing the execution of a given code part quite simply! Just employ *call_later()* method, which is available in class *Agent()*.


Using call_later() method
-----------------------------------

In order to use *call_later()* properly, the following parameters must be specified: delay type, method supposed to be called after such time interval and its respective argument using the following syntax: *call_later(time, method, *args)*.

The following code employs call_later() in classe Sender() using on_start() method to ensure that all agents are launched in the platform, thus initializing send_message() 4.0 seconds after the execution of agents:

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
            self.call_later(4.0, self.send_message)

        def send_message(self):
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
