Active Source Passive Sink
==========================

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by a passive packet sink
(:ned:`PassivePacketSink`).

.. figure:: media/ActiveSourcePassiveSink.png
   :width: 50%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network ProducerConsumerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config ActiveSourcePassiveSink
   :end-at: productionInterval
   :language: ini
