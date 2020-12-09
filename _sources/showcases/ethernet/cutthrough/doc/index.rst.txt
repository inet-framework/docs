Ethernet Cut-Through Switching
==============================

Goals
-----

.. so

  - cut-through switching can reduce latency of ethernet frames
  - works best when the frame goes through a lot of switches
  - cut-through switching (start forwarding the frame on another interface as soon as the header is received, and the next-hop address is available, as opposed to receive the whole packet and forward after that)
  - the new composable/layered ethernet model supports packet streams and cutthrough switching

Cut-through switching can reduce switching delay of Ethernet frames by immediately forwarding an Ethernet frame after the header is received and the switch knows which outgoing interface to send the frame on (as opposed to store-and-forward switching, in which the whole frame is received and then forwarded).

.. **TODO** which outgoing interface to use/to send the frame on

.. This showcase demonstrates cut-through switching, and compares its delay with store-and-forward switching.

This showcase demonstrates cut-through switching, and compares it to store-and-forward switching in terms of delay.

| INET version: ``4.3``
| Source files location: `inet/showcases/ethernet/cutthrough <https://github.com/inet-framework/inet-showcases/tree/master/ethernet/cutthrough>`__

.. The new composable/layered Ethernet model supports cut-through switching.

The Model
---------

.. - cut through switching reduces delay
   - it skips the FCS check (its handles in the endpoints)
   - it requires packet streams (also enables preemption)
   - need LayeredEthernetInterface, and CuttroughEthernetInterface in switches

.. **TODO** works best when the frame goes through a lot of switches

Cut-through switching reduces switching delay, but skips the FCS check, as the FCS is at the end of the Ethernet frame; the FCS check is performed in at destination host. The delay reduction is more substantial if the packet goes through multiple switches (as one packet transmission duration can be saved at each switch).

Cut-through switching makes use of intra-node  packet streaming in INET's modular Ethernet model.
Packet streaming is required because the frame needs to be processed as a stream (as opposed to as a whole packet) in order for the switch to be able to start forwarding it before the whole packet is received.

.. **TODO** store-and-forward is the default

.. note:: The default is store-and-forward behavior in hosts such as :ned:`StandardHost`.

The example simulation contains two :ned:`StandardHost` nodes connected by two :ned:`EthernetSwitch`' nodes (all connections are 1 Gbps):

.. image:: media/Network.png
   :align: center
   :width: 100%

.. **TODO** 1Gbps connection

.. There are two configurations in omnetpp.ini. In both of them, host1 sends UDP packets to host2.

In the simulation, host1 sends 1000-Byte UDP packets to host2, with a mean arrival time of 100ms, and X ms jitter. There are two configurations in omnetpp.ini, ``StoreAndForward`` and ``Cutthrough`` (only differing in the use of cut-through switching).

**TODO** NoCuttrough -> StoreAndForward; - in config name (try)

.. In the ``General`` configuration,

.. Here is the part from the ``General`` configuration concerning Ethernet:

In the ``General`` configuration, the following lines configure the hosts and switches to use the modular Ethernet model:

.. **TODO** typename = DropTailQueue

.. **TODO** ini-be -> NoCuttrough -> #default behavior, no configuration required

.. literalinclude:: ../omnetpp.ini
   :start-at: *.*.encap.typename
   :end-at: LayeredEthernetInterface
   :language: ini

The encapsulation type :ned:`OmittedEthernetEncapsulation` is there for backward compatibility purposes;
it's a dummy encapsulation module required by the new layered Ethernet model so that it is a drop-in replacement for the old one).

.. **TODO** dummy encapsulation/decapsulation module required by the new modular/layered ethernet model (its needed so that the new model is a drop-in replacement for the old one)

Also, the link speed is specified:

.. literalinclude:: ../omnetpp.ini
   :start-at: bitrate
   :end-at: bitrate
   :language: ini

To prevent packets from accumulating in the queue of the sender host (and thus increasing the measured end-to-end delay), the queue is limited to one packet.

.. , and configured to drop packets from the end of the queue:

.. literalinclude:: ../omnetpp.ini
   :start-at: packetCapacity
   :end-at: dropperClass
   :language: ini

Here are the two configurations:

.. literalinclude:: ../omnetpp.ini
   :start-at: StoreAndForward
   :end-at: phyLayer
   :language: ini

.. - the cuttroughinterface is needed for the cuttrough
   - the streamingphylayer is needed also for that cuttrough (it needs to support packet streaming)(the cuttroughinterface does that by default)

The cut-through interface in the switches support packet streaming by default; the :ned:`EthernetStreamingPhyLayer` in the hosts support packet streaming as well.

Results
-------

.. - qtenv
   - seqchart
   - chart

.. Here is a video of the cut-through behavior in Qtenv:

.. Here is a video of the store-and-forward behavior in Qtenv:

The following videos store-and-forward and cut-through behavior in Qtenv, respectively:

.. **TODO** store and forward video; disable arp

.. video:: media/storeandforward.mp4
   :width: 100%
   :align: center

.. video:: media/cutthrough1.mp4
   :width: 100%
   :align: center

.. .. note:: The ARP request is broadcast, so it is not utilizing cut-through.

The following sequence chart excerpt shows a packet sent from host1 to host2 via the switches, for store-and-forward and cut-through, respectively (the timeline is linear):

.. **TODO** linear time

.. **TODO** seq chart store and forward

.. **TODO** azert vannak kiugrok mert 1 csomag tud varakozni a queue-ban; vagy change the rate (ritkabban)

.. image:: media/storeandforwardseq2.png
   :align: center
   :width: 100%

.. image:: media/seqchart2.png
   :align: center
   :width: 100%

We compared the end-to-end delay of the UDP packets in the case of store-and-forward switching vs cut-through switching:

.. image:: media/delay.png
   :align: center
   :width: 100%

.. **TODO** szamolgatas; n*transmission duration + 3 propagation time; 1 transmission + 3 propagation + 2 cuttrough (header reception)(cuttrough delay)

We can verify that result analytically. In case of store-and-forward, the end-to-end duration is ``3 * (transmission time + propagation time)``, around 25.296 ms. In the case of cut-through, the duration is ``1 * transmission time + 3 propagation time + 2 * cut-through delay``, around 8.432 ms.

Sources: :download:`omnetpp.ini <../omnetpp.ini>`, :download:`EthernetCutthroughShowcase.ned <../EthernetCutthroughShowcase.ned>`

Discussion
----------

Use `this <https://github.com/inet-framework/inet-showcases/issues/TODO>`__ page in the GitHub issue tracker for commenting on this showcase.

.. 1054B; 8.432us; 25.296+propagation time

  (1000 + 8 + 20 + 18 + 8) * 8 / 1E+9 * 3 / 1E-6
  (1000 + 8 + 20 + 18 + 8) * 8 / 1E+9 / 1E-6 + 22 / 1E+9 / 1E-6 * 2
