Step 3. Link Breakage
=====================

Goals
-----

TODO: routes will be added by RIP...then a link break is scheduled by
:ned:`ScenarioManager`. SplitHorizon is enabled. RIP should update the
routes to indicate that the link is broken

The model
---------

TODO: what is SplitHorizon

This step uses the same network as the previous one.

The configuration in ``omnetpp.ini`` is the following:

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step3
   :end-before: ------

The scenario manager script:

.. literalinclude:: ../scenario2.xml
   :language: xml

Results
-------

TODO: video

.. video:: media/step3_linkbreak.mp4
   :width: 100%

..   <!--internal video recording, normal run from 31s to 71+s, animation speed none, playback speed 2.138-->

TODO: what happens

TODO: maybe routing tables and screenshots of RIP packets

Sources:
:download:`omnetpp.ini <../omnetpp.ini>`,
:download:`RipNetworkA.ned <../RipNetworkA.ned>`,
:download:`scenario2.xml <../scenario2.xml>`
