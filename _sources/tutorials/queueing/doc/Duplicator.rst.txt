Duplicator
==========

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The produced packets are randomly either duplicated or not
(:ned:`PacketDuplicator`). Finally, the packets are all sent into a passive packet
sink (:ned:`PassivePacketSink`).

.. figure:: media/Duplicator.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network DuplicatorTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Duplicator
   :end-at: numDuplicates
   :language: ini
