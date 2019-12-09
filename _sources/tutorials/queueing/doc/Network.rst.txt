Simplistic Network
==================

This step demonstrates combining queueing components to create a simplistic network.
The network features two hosts (ExampleHost) communicating. The hosts are connected by a cable module (ExampleCable) which
adds delay to the connection. Each host contains a packet source and a packet sink application,
connected to the network level by an interface module (ExampleInterface).

.. figure:: media/Network_TestCable.png
   :width: 30%
   :align: center

.. figure:: media/Network.png
   :width: 50%
   :align: center

.. figure:: media/Network_TestHost.png
   :width: 60%
   :align: center

.. figure:: media/NetworkInterface.png
   :width: 50%
   :align: center

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: network ExampleNetworkTutorialStep
   :end-before: //----
   :language: ned

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: module ExampleHost
   :end-before: //----
   :language: ned

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: module ExampleInterface
   :end-before: //----
   :language: ned

.. literalinclude:: ../QueueingTutorial.ned
   :start-at: module ExampleCable
   :end-before: //----
   :language: ned

.. literalinclude:: ../omnetpp.ini
   :start-at: Config ExampleNetwork
   :end-at: delay
   :language: ini
