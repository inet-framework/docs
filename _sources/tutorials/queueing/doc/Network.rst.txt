Example: Simulating a Simplistic Network
========================================

This example network demonstrates how queueing components can be combined to
create a simplistic network with two network nodes, connected by a point-to-point link 
with a finite bit rate. (This is only interesting as a demonstration of the power 
of the queueing library, network links are never actually simulated like this in 
OMNeT++ or INET.)

The network features two hosts (``ExampleHost``) communicating. The hosts are
connected by a cable module (``ExampleCable``) which adds delay to the connection.
Each host contains a packet source and a packet sink application, connected to
the network level by an interface module (``ExampleInterface``).

.. image:: media/Network_TestCable.png
   :width: 30%
   :align: center

.. image:: media/Network.png
   :width: 50%
   :align: center

.. image:: media/Network_TestHost.png
   :width: 60%
   :align: center

.. image:: media/NetworkInterface.png
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
