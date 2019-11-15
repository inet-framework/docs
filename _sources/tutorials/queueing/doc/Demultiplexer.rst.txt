Demultiplexer
=============

In this step, packets are collected periodically (randomly) by several active
packet sinks (:ned:`ActivePacketSinks`). The packets are provided by a single passive
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
