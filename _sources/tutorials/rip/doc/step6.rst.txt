Step 6. Counting to Infinity (Two-node loop instability)
========================================================

Goals
-----

TODO: The link breaks, and in the RIP updates the hop count gets
gradually larger -> counting to infinity it reaches 16 (unusable) but it
takes lots of minutes

The model
---------

TODO: how this can be prevented (SplitHorizon, etc)

This step uses the following network:

.. literalinclude:: ../RipNetworkC.ned
   :language: ned
   :start-at: RipNetwork

The configuration in ``omnetpp.ini`` is the following:

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step6
   :end-before: ------

The scenario manager script:

.. literalinclude:: ../scenario4.xml
   :language: xml

**Solution 1:**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step6Solution1
   :end-before: ------

**Solution 2:**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step6Solution2
   :end-before: ------

**Solution 3:**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step6Solution3
   :end-before: ------

**Different Timings:**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step6DifferentTimings
   :end-before: ------


Results
-------

TODO: video

Rip convergence takes 220 seconds (from link break at 50s to no routes
to host3 at 270s). Note the incrementally increasing hop count
(indicated on the route in parentheses), i.e. counting to infinity

.. video:: media/step6_1.mp4
   :width: 100%

..   <!--internal video recording, zoom 0.77, playback speed 1, no animation speed-->

Rip start, link break, counting to infinity, ping packets:

.. video:: media/step6_2.mp4
   :width: 100%

Ping packets go back and forth between the two routers, indicating the
presence of the routing loop. The ping packet times out after 8 hops,
and then it's dropped.

TODO: what happens

TODO: screenshots of routing tables / RIP packets

Sources:
:download:`omnetpp.ini <../omnetpp.ini>`,
:download:`RipNetworkC.ned <../RipNetworkC.ned>`,
:download:`scenario4.xml <../scenario4.xml>`
