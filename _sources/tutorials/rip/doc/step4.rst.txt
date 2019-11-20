Step 4. RIP Timeout timer and garbage-collection timer
======================================================

Goals
-----

TODO: Demonstrating the timeout-timer and the garbage collection timer

The model
---------

TODO: about the timout-timer and garbage collection timer... mark routes
as expired after 180s inactivity by default, delete them after 120s (but
still advertise until deleted)

This step uses the following network:

.. literalinclude:: ../RipNetworkB.ned
   :language: ned
   :start-at: RipNetwork

The configuration in ``omnetpp.ini`` is the following:

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step4
   :end-before: ------

The scenario manager script:

.. literalinclude:: ../scenario1.xml
   :language: xml

**Variant "A":**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step4A
   :end-before: ------

The scenario manager script:

.. literalinclude:: ../scenario5.xml
   :language: xml

**Variant "B":**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step4B
   :end-before: ------

The scenario manager script:

.. literalinclude:: ../scenario6.xml
   :language: xml

**Variant "C":**

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step4C
   :end-before: ------

The scenario manager script:

.. literalinclude:: ../scenario6.xml
   :language: xml


Results
-------

TODO: video

.. video:: media/step4.mp4
   :width: 100%

Here are two images of the RIP table of ``router1``.

The link breaks at 50s, so ``router1`` doesn't receive any updates on
the route to the 10.0.0.24/29 network from ``router2``. As indicated on
the following image, the last update to the route was at 30s, thats when
the timeout timer was started.

.. figure:: media/step4_3.png
   :width: 80%
   :align: center

The timeout timer expires at 210s, the route is set to metric 16, and
the flush timer is started.

.. figure:: media/step4_4.png
   :width: 80%
   :align: center

The flush timer expires at 330s, and the route is removed from the RIP
table.

TODO: what happens

TODO: screenshots or routing tables / RIP packets

Sources:
:download:`omnetpp.ini <../omnetpp.ini>`,
:download:`RipNetworkB.ned <../RipNetworkB.ned>`,
:download:`scenario1.xml <../scenario1.xml>`,
:download:`scenario5.xml <../scenario5.xml>`,
:download:`scenario6.xml <../scenario6.xml>`
