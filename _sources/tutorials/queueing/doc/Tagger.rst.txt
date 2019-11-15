Tagger
======

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets pass through a packet tagger which attaches
a HopLimitReq tag. The packets are consumed by a passive packet sink (:ned:`PassivePacketSink`).

.. figure:: media/Tagger.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network TaggerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Tagger
   :end-at: hopLimit
   :language: ini
