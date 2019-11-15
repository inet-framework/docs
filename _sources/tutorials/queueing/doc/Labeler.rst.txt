Labeler
=======

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by two passive packet sinks
(:ned:`PassivePacketSinks`). The single source is connected to the two sinks using a
classifier (:ned:`LabelClassifier`). The classifier forwards packets alternately to
one or the other sink based on the packet's label. The label is attached by
a PacketLabeler based on the packet length.

.. figure:: media/Labeler.png
   :width: 90%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network LabelerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Labeler
   :end-at: labelsToGateIndices
   :language: ini
