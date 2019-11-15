Step 13. Freshness of a LSA
===========================

Goals
-----

[explanation]

Configuration
~~~~~~~~~~~~~

This step uses the following network:

.. figure:: media/step13.png
   :width: 100%
   :align: center

.. literalinclude:: ../Freshness.ned
   :start-at: network Freshness
   :language: ned

The configuration in ``omnetpp.ini`` is the following:

.. literalinclude:: ../omnetpp.ini
   :language: ini
   :start-at: Step13
   :end-before: ------

The scenario script:

.. literalinclude:: ../scenario_fresh.xml
   :language: xml

Results
~~~~~~~

[explanation]

Sources:
:download:`omnetpp.ini <../omnetpp.ini>`,
:download:`Freshness.ned <../Freshness.ned>`,
:download:`scenario_fresh.xml <../scenario_fresh.xml>`

Discussion
----------

Use `this page <https://github.com/inet-framework/inet-tutorials/issues/TODO>`__ in
the GitHub issue tracker for commenting on this tutorial.

