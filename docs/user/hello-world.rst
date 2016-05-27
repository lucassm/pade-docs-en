Hello, world!
=============

PADE was created with a main purpose: simplicity!

After PADE is installed in your PC, it is quite simple to start using it.

In a given folder, create a file called *start_mas.py* by using your favorite text editor. Then type (or copy and paste) the following code inside it:

::

    # this is file start_mas.py
    from pade.misc.common import set_ams, start_loop

    if __name__ == '__main__':
        set_ams('localhost', 8000)
        start_loop(list(), gui=True)

You will see a graphic interface like this:

.. figure:: ../img/InterfaceSniffer.png
    :align: center
    :width: 5.0in
    



    
