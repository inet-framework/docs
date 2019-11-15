Filter 1
========

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by a passive packet sink (:ned:`PassivePacketSink`).
Packets are passed through from the source to the sink by a filter (:ned:`ContentBasedFilter`).
Every second packet is dropped.

.. figure:: media/Filter1.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network Filter1TutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Filter1
   :end-at: packetFilter
   :language: ini
