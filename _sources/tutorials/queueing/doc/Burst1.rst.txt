Burst 1
=======

In this step, packets are periodically (randomly) produced by two active sources
(:ned:`ActivePacketSources`). One source produces packets with a slower rate while the other
source uses a faster rate. The two packet sources are combined using a markov
chain with random transition matrix and random wait intervals. The packets are
consumed by a single passive sink (:ned:`PassivePacketSink`).

.. figure:: media/Burst1.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network Burst1TutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Burst1
   :end-at: waitIntervals
   :language: ini
