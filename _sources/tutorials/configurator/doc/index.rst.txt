IPv4 Network Configurator Tutorial
==================================

This tutorial shows how one can configure IP addresses and routing tables in wired
and wireless networks in the INET Framework without using a host configuration
protocol and a routing protocol; that is, how to achieve static autoconfiguration.

In INET simulations, configurator modules are commonly used for assigning IP
addresses to network nodes and for setting up their routing tables. There are
various configurators modules in INET. This tutorial covers the most generic and
most featureful one, :ned:`Ipv4NetworkConfigurator`. It supports automatic and
manual network configuration, and their combinations. By default, the
configuration is fully automatic. When automatic configuration does not yield
the desired results, the user can specify manual configuration for parts (or
all) of the network, and the rest will be configured automatically. The
configurator's various features can be turned on and off with parameters. The
details of the configuration, such as IP addresses and routes, can be specified
in an XML file.

.. Essentially, the configurator module simulates a real life network administrator.
   The configurator assigns IP addresses to interfaces, and sets up static routing in IPv4 networks.
   It doesn't configure IP addresses and routes directly, but stores the configuration in its internal data structures.
   Network nodes contain an instance of :ned:`Ipv4NodeConfigurator`, which configures the corresponding node's interface table and routing table based on information contained in the global :ned:`Ipv4NetworkConfigurator` module.
   The purpose of this design is that when router reboots after a simulated failure or shutdown,
   this way it can pull its IPv4 configuration from the configurator module, and restore
   its IPv4 addresses and routing table.

The tutorial is organized into several steps, each one demonstrating
a different feature or use case for the network configurator:

.. toctree::
   :maxdepth: 1
   :glob:

   step?
   step1?
   conclusion

This is an advanced tutorial, and it assumes that you are familiar with
creating and running simulations in OMNeT++ and INET. If you aren't,
please read the INET User's Guide first.