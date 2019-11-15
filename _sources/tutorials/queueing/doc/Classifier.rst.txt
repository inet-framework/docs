Classifier
==========

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by two passive packet sinks
(:ned:`PassivePacketSinks`). The single source is connected to the two sinks using a
classifier (:ned:`PacketClassifier`). The classifier forwards packets alternately to
one or the other sink.

.. figure:: media/Classifier.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network ClassifierTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Classifier
   :end-at: weights
   :language: ini
