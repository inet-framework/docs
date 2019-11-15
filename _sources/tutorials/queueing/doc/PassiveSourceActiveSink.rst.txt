Passive Source Active Sink
==========================

In this step, packets are collected periodically by an active packet sink
(:ned:`ActivePacketSink`). The packets are provided by a passive packet source
(:ned:`PassivePacketSource`).

.. figure:: media/PassiveSourceActiveSink.png
   :width: 60%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network ProviderCollectorTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config PassiveSourceActiveSink
   :end-at: collectionInterval
   :language: ini
