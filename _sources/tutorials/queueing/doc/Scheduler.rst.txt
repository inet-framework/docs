Scheduler
=========

In this step, packets are collected periodically by an active packet sink
(:ned:`ActivePacketSink`). The packets are produced by two passive packet sources
(:ned:`PassivePacketSources`). The single sink is connected to the two sources using a
scheduler (:ned:`WrrScheduler`). The scheduler forwards packets alternately from
one or the other source.

.. figure:: media/Scheduler.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network SchedulerTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config Scheduler
   :end-at: weights
   :language: ini
