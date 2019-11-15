Delayer
=======

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The produced packets are delayed (:ned:`PacketDelayer`) for a random
amount of time. Finally, the packets are sent into a passive packet sink (:ned:`PassivePacketSink`).

.. figure:: media/Delayer.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network DelayerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Delayer
   :end-at: uniform
   :language: ini
