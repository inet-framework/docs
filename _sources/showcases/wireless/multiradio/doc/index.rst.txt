:orphan:

Multiradio
==========

Goals
-----

In reality, devices often have more than one wireless interface (for
example, a dual band wireless router has two radios.) Wireless nodes in
INET can have multiple interfaces as well. This showcase contains an
example simulation, in which nodes communicate via a router, which has
two wireless interfaces.

INET version: ``4.0``
Source files location: `inet/showcases/wireless/infrastructure <https://github.com/inet-framework/inet-showcases/tree/master/wireless/infrastructure>`__

The model
---------

.. todo::

   <!--
   - by default, most hosts in INET have just one radio
   - but the number of radios can be set by a parameter
   - actually, you can build any kind of host with any number of radios
   - but it is easy by setting the numWlanIntefaces parameter
   - i think even StandardHost has one
   - it is part of the LinkLayerNodeBase
   -->

   <!--
   INET's wireless host types have one wlan interface by default.
   The number of wlan interfaces in a host is specified by the host's `numWlanInterfaces` parameter.
   The parameter's default value is 1 for wireless hosts, such as `WirelessHost` and `AdhocHost`,
   and 0 for `StandardHost`.
   -->

The number of wlan interfaces in INET's host types is specified by the
host's ``numWlanInterfaces`` parameter. The parameter's default value is
1 for wireless hosts, such as ``WirelessHost`` and ``AdhocHost``, and 0
for ``StandardHost``. (``numWlanInterfaces`` is actually the parameter
of ``LinkLayerNodeBase``, on which these host types are built.) However,
one can build a custom host type from scratch with an arbitrary number
of radio interfaces in the NED file.

The configuration
~~~~~~~~~~~~~~~~~

The example simulation for this showcase uses the following network:

.. figure:: network.png
   :width: 100% 

The network contains two ``WirelessHost``\ s named ``host1`` and
``host2``, two ``accessPoint``\ s (``accessPoint1`` and
``accessPoint2``), and a ``Router``. The network also contains an
``Ipv4NetworkConfigurator``, an ``Ieee80211ScalarRadioMedium`` and an
``IntegratedVisualizer`` module.

.. todo::

   <!--
   By default, INET's wireless host types (such as `WirelessHost` and `AdhocHost`) have one
   wlan interface.
   -->

   <!--
   - TODO: using 802.11
   - the router has two radios operating on different channels
   - the hosts are configured to ping each other
   - the scenario is that each host uses a different channel
   - each host connects to one of the access points
   - the access points are connected to the router...one of the radios of the router
   - actually, the router connects to each access point with each of its radios
   - the managementtype is set to simplified
   - the routes are configured
   - the visualizers are configured -> is this needed?
   -->

The access points are configured to create wireless networks on
different channels. Each host is configured to associate with the nearby
access point. The router will have two wireless interfaces, and will
connect to both access points with one of its interfaces. The router
will connect the two wireless networks by relaying packets between them.
``host1`` will ping ``host2``.

.. todo::

   <!--
   The two access points will create wireless networks on different channels. `host1`
   will be associated with `accessPoint1`, and `host2` with `accessPoint2`. The router
   will connect to both networks, using one of its radio interfaces for each network.
   `host1` is configured to ping `host2`. The ping packets will go through the router.
   -->

   <!--
   All nodes are configured to use simplifies management modules, thus all hosts are
   assumed to be already connected to the wireless network at the start of the simulation.
   -->

``accessPoint1`` is configured to create the wireless network on channel
0, and ``accessPoint2`` on channel 1. ``host1`` is configured to be
connected to ``accessPoint1``, and ``host2`` to ``accessPoint2``. The
number of radios in ``router`` is set to two, and each radio is
configured to connect to one of the wireless networks.


.. todo::

   <!--
   Because of the simplified management, the MAC addresses of the access points need
   to be set in hosts' management modules in order for them to be associated with the
   specified access point.-->

The following keys from the ini file shows the configuration of the
wireless networks:

.. literalinclude:: ../omnetpp.ini
   :start-at: access point
   :end-before: application level

Setting the ``numChannels`` parameter is essential for the station
nodes, because it tells the management module the number of channels to
scan, starting for channel 0. We're using two channels here, 0 and 1.
Since we're using two channels (0 and 1), the stations wouldn't find the
wireless network on channel 1 if the ``numChannels`` parameter were left
at its default setting, 1.

.. todo::

   <!-- :download:[omnetpp.ini](../omnetpp.ini) -->

   <!--TODO: visualizer config ? -> or just at the results section-->

   <!--
   the router acts as a gateway between the two wireless networks
   host one has a route: for all destinations, the router should be the gateway
   so host1 wants to send a packet to host2, the gateway is the router
   which is connected to the same accesspoint
   -->

Routing is set up by the ``Ipv4NetworkConfigurator`` module. The routing
tables of both hosts are configured to use one of the router's
interfaces as gateway for reaching all destinations. The routing table
of the router is configured to use its appropriate interface for
reaching each wireless network.

The routes are shown on the following image. Note that the routing
arrows don't go through the access points because they are only L2
devices, but the packets will go through them.

.. figure:: routes.png
   :width: 100% 

Results
-------

``host1`` is pinging ``host2`` through the accessPoints and the router
in the following video. Successful transmissions between nodes' data
link layers are visualized. The transmissions for the two different
networks are colored differently (red for AP1 and blue for AP2.)

.. video:: Multiradio1.mp4
   :width: 698

   <!--internal video recording, animation speed none, run until 1.8s-->

Sources: :download:`omnetpp.ini <../omnetpp.ini>`, :download:`MultiRadioShowcase.ned <../MultiRadioShowcase.ned>`

.. todo::

   comments on this showcase
