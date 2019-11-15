Multiplexer
===========

In this step, packets are produced periodically (randomly) by several active
packet sources (:ned:`ActivePacketSources`). The packets are consumed by a single passive
packet sink upon arrival (:ned:`PassivePacketSink`). The single sink is connected to the
multiple sources using an intermediary component (:ned:`PacketMultiplexer`) which simply
forwards packets.

.. figure:: media/Multiplexer.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network MultiplexerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Multiplexer
   :end-at: productionInterval
   :language: ini
