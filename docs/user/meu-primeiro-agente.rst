My first agent
==============

Now it is time to create a real agent!

Creating my first agent
-----------------------

In order to create your first agent, open your favorite text editor and type (or copy and paste) the following code:

::

    from pade.misc.utility import display_message
    from pade.misc.common import set_ams, start_loop
    from pade.core.agent import Agent
    from pade.acl.aid import AID


    class AgenteHelloWorld(Agent):
        def __init__(self, aid):
            super(AgenteHelloWorld, self).__init__(aid=aid, debug=False)
            display_message(self.aid.localname, 'Hello World!')

    if __name__ == '__main__':

        set_ams('localhost', 8000, debug=False)

        agents = list()

        agente_hello = AgenteHelloWorld(AID(name='agente_hello'))
        agente_hello.ams = {'name': 'localhost', 'port': 8000}
        agents.append(agente_hello)

        start_loop(agents, gui=True)


This is an agent, but it is not quite useful at all, is it? It can be only run once. :(

The following question remains: how is it possible to create an agent whose behavior is run from time to time?
