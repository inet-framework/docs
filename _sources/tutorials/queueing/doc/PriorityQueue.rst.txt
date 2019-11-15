Priority Queue
==============

In this step, packets are produced periodically (randomly) by an active packet
source (:ned:`ActivePacketSource`). The packets are collected periodically (randomly) by
an active packet sink (:ned:`ActivePacketSink`). The source and the sink is connected
by a priority queue with two inner queues (:ned:`PriorityQueue`) where packets are
stored temporarily.

.. figure:: media/PriorityQueue.png
   :width: 70%
   :align: center

.. figure:: media/PriorityQueue_Queue.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network PriorityQueueTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config PriorityQueue
   :end-at: collectionInterval
   :language: ini
