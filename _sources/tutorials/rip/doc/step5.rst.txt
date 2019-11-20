Step 5. RIP Triggered Update
============================

Goals
-----

TODO: triggered updates are turned on, routers should be notified of
link break sooner

The model
---------

TODO: how triggered updates work (maybe should be described in an
earlier step?)

This step uses the same network as the previous one.

The configuration in ``omnetpp.ini`` is the following:

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step5
   :end-before: ------

Results
-------

TODO: video

Triggered updates are enabled, so other routers are notified of the
broken link right after it breaks (around 52s), not after the next
scheduled update (at 60s).

.. video:: media/step5.mp4
   :width: 100%

..   <!--internal video recording, zoom 0.77, animation speed none, playback speed 2.138, from 30s to 60s-->

TODO: what happens

TODO: screenshots of routing tables / RIP packets

Sources:
:download:`omnetpp.ini <../omnetpp.ini>`,
:download:`RipNetworkB.ned <../RipNetworkB.ned>`
