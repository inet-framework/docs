Server
======

In this step, packets are passed through from the source to the sink periodically
(randomly) by an active packet processor (:ned:`PacketServer`). The packets are generated
by a passive packet source (:ned:`PassivePacketSource`) and consumed by a passive packet sink
(:ned:`PassivePacketSink`).

.. figure:: media/Server.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network ServerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Server
   :end-at: processingTime
   :language: ini
