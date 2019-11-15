Packet Queue
============

In this step, packets are produced periodically (randomly) by an active packet
source (:ned:`ActivePacketSource`). The packets are collected periodically (randomly) by
an active packet sink (:ned:`ActivePacketSink`). The source and the sink is connected
by a FIFO queue (:ned:`PacketQueue`) where packets are stored temporarily.

.. figure:: media/PacketQueue.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network PacketQueueTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config PacketQueue
   :end-at: collectionInterval
   :language: ini
