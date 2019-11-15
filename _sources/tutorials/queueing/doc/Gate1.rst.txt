Gate1
=====

In this step, packets are produced periodically by an active packet source
(:ned:`ActivePacketSource`). The packets pass through a packet gate if it's open,
otherwise packets are not generated. The packets are consumed by a passive
packet sink (:ned:`PassivePacketSink`).

.. figure:: media/Gate1.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network Gate1TutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Gate1
   :end-at: closeTime
   :language: ini
