Priority Classifier
===================

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by two active packet sinks
(:ned:`ActivePacketSinks`). The sinks are connected to FIFO queues (:ned:`PacketQueue`) with
limited capacity where packets are stored temporarily. The single source is
connected to the two queues using a classifier (:ned:`PriorityClassifier`). The
classifier forwards packets from the producer to the queues in a prioritized
way.

.. figure:: media/PriorityClassifier.png
   :width: 90%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network PriorityClassifierTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config PriorityClassifier
   :end-at: collectionInterval
   :language: ini
