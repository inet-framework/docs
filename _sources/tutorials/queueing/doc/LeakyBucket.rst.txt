Leaky Bucket
============

In this step, packets are produced by an active packet source (:ned:`ActivePacketSource`).
The packet source pushes packets into a leaky bucket module, which pushes them into
a passive packet sink (:ned:`PassivePacketSink`).

.. figure:: media/LeakyBucket.png
   :width: 60%
   :align: center

.. figure:: media/LeakyBucket_Bucket.png
   :width: 65%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network LeakyBucketTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config LeakyBucket
   :end-at: processingTime
   :language: ini
