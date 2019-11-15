Meter
=====

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets are consumed by a passive packet sink
(:ned:`PassivePacketSink`). The packet rate is measured and if the rate of packets
is higher than a predefined threshold, then packets are dropped.

.. figure:: media/Meter.png
   :width: 90%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network MeterTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Meter
   :end-at: maxPacketrate
   :language: ini
