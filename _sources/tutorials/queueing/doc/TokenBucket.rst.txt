Token Bucket
============

In this step, packets are produced periodically by an active packet source (:ned:`ActivePacketSource`).
The packets are pushed to a token bucket module (:ned:`TokenBucket`). A token generator (:ned:`TimeBasedTokenGenerator`)
generates tokens periodically into the token bucket module. When the token bucket has sufficient
tokens, it emits a packet into a passive packet sink (:ned:`PassivePacketSink`).

.. figure:: media/TokenBucket.png
   :width: 60%
   :align: center

.. figure:: media/TokenBucket_Bucket.png
   :width: 80%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network TokenBucketTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config TokenBucket
   :end-at: generationInterval
   :language: ini
