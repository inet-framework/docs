Ordinal Based Duplicator
========================

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by a passive packet sink (:ned:`PassivePacketSink`).
Packets are passed through from the source to the sink by a duplicator (:ned:`OrdinalBasedDuplicator`).
Every second packet is duplicated based on its ordinal number.

.. figure:: media/OrdinalBasedDuplicator.png
   :width: 60%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network OrdinalBasedDuplicatorTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config OrdinalBasedDuplicator
   :end-at: duplicatesVector
   :language: ini
