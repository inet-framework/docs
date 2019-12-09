Demultiplexer
=============

.. This step demonstrates the :ned:`PacketDemultiplexer` module. On request, the module pops packets
   from the provider connected to its input, and forwards it to the collector connected to one
   of its outputs.

The :ned:`PacketDemultiplexer` module connects to a passive packet source
on its input and multiple active packet sinks on its outputs. When one of the collectors requests a packet
from the demultiplexer, it pops a packet from the provider and forwards it to the collector.

In this step, packets are collected at random intervals by several active
packet sinks (:ned:`ActivePacketSink`). The packets are provided by a single passive
packet source upon request (:ned:`PassivePacketSource`). The single source is connected to
the multiple sinks using an intermediary component (:ned:`PacketDemultiplexer`) which
simply forwards packets.

.. figure:: media/Demultiplexer.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network DemultiplexerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Demultiplexer
   :end-at: collectionInterval
   :language: ini
