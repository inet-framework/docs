Compound Queue
==============

In this step, packets are produced periodically (randomly) by an active packet
by a compound priority queue (TestCompoundPacketQueue) where packets are stored temporarily.
source (:ned:`ActivePacketSource`). The packets are collected periodically (randomly) by
an active packet sink (:ned:`ActivePacketSink`). The source and the sink is connected
This queue contains a classifier (:ned:`PacketClassifier`), two queues (:ned:`PacketQueue`),
and a priorty scheduler (:ned:`PriortyScheduler`).

.. figure:: media/CompoundQueue.png
   :width: 70%
   :align: center

.. figure:: media/CompoundQueue_Queue.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network CompoundPacketQueueTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: module TestCompoundPacketQueue
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config CompoundQueue
   :end-at: weights
   :language: ini
