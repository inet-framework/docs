Step 1. Static routing
======================

Goals
-----

In this step, RIP is not used, all IPv4 routes are assigned statically
by the :ned:`Ipv4NetworkConfigurator` module.

The model
---------

The configuration uses the following network:

.. figure:: media/step1network.png
   :width: 80%
   :align: center

TODO: the network contains three LANs, connected to a network of routers
via ethernet switches

TODO: In the simulation, a host from one subnet will ping a host in
another subnet. The ping packets will be routed via the routers, which
use static routes assigned by :ned:`Ipv4NetworkConfigurator`.

The configuration in is the following:

.. literalinclude:: ../omnetpp.ini
   :start-at: Step1
   :end-before: ----
   :language: ini

Results
-------

The following image shows the routes towards ``host0`` as red arrows,
and towards ``host6`` as blue arrows:

.. figure:: media/step1routes.png
   :width: 80%
   :align: center

Here is a video of ``host0`` pinging ``host6``:

.. video:: media/step1_2.mp4
   :width: 100%

..   <!--internal video recording, animation speed none, playback speed 2.138, zoom 0.77-->


