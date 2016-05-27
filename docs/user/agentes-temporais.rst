Time agents
===========

In real applications the agent behavior is typically run from time to time, and not only once. How is it possible to implement it in PADE? :(

Running a time agent
--------------------

This is the example of an agent that runs indefinitely at 1.0-second intervals.

::

    #!coding=utf-8
    # Hello world temporal in PADE!
    #
    # Criado por Lucas S Melo em 21 de julho de 2015 - Fortaleza, Ceará - Brasil

    from pade.behaviours.protocols import TimedBehaviour
    from pade.misc.utility import display_message
    from pade.misc.common import set_ams, start_loop
    from pade.core.agent import Agent
    from pade.acl.aid import AID


    class ComportTemporal(TimedBehaviour):
        def __init__(self, agent, time):
            super(ComportTemporal, self).__init__(agent, time)

        def on_time(self):
            super(ComportTemporal, self).on_time()
            display_message(self.agent.aid.localname, 'Hello World!')


    class AgenteHelloWorld(Agent):
        def __init__(self, aid):
            super(AgenteHelloWorld, self).__init__(aid=aid, debug=False)

            comp_temp = ComportTemporal(self, 1.0)

            self.behaviours.append(comp_temp)


    if __name__ == '__main__':

        set_ams('localhost', 8000, debug=False)

        agents = list()

        agente_1 = AgenteHelloWorld(AID(name='agente_1'))
        agente_1.ams = {'name': 'localhost', 'port': 8000}

        agents.append(agente_1)

        start_loop(agents, gui=True)

Running two time agents
-----------------------

What if two agents with the same behavior are necessary? No problem at all. Just instantiate another agent with the same class.

::

    if __name__ == '__main__':

        set_ams('localhost', 8000, debug=False)

        agents = list()

        agente_1 = AgenteHelloWorld(AID(name='agente_1'))
        agente_1.ams = {'name': 'localhost', 'port': 8000}

        agente_2 = AgenteHelloWorld(AID(name='agente_2'))
        agente_2.ams = {'name': 'localhost', 'port': 8000}

        agents.append(agente_1)
        agents.append(agente_2)

        start_loop(agents, gui=True)

