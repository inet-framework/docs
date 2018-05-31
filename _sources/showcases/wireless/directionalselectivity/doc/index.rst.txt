:orphan:

Directional Selectivity of Antennas
===================================

.. todo::

   TODO: antennas or antennae

keywords: directional characteristics, radiation pattern,
directionality, directional selectivity, gain, lobes,

radiation pattern -> depiction of directional characteristics

Goals
-----



.. <!-- INET contains several different antenna models -->

INET contains various isotropic, omnidirectional and directional antenna
models. The support for different antennas is useful for simulating many
kinds of wireless scenarios, as antenna characteristics are important
for wireless connectivity.

as wireless connectivity can often depend on antenna characteristics

INET contains various antenna modules, such as the isotropic antenna,
which has no directionality, or the high-gain parabolic antenna.

TODO

This showcase aims to highlight the antenna models available in INET,
and their directional characteristics. The showcase contains an example
simulation which demonstrates the direcionality of four antenna models.

INET version: ``4.0``\  Source files location:
```inet/showcases/wireless/antennadirection`` <https://github.com/inet-framework/inet-showcases/tree/master/general/mobility>`__

Concepts
--------

In INET, radio modules contain transmitter, receiver, and antenna
submodules. The success of receiving a wireless transmission depends on
the strength of the signal present at the receiver, among other things,
such as interference from other signals. Both the transmitter and the
receiver submodules use the antenna submodules when sending and
receiving transmissions. Actually, the antenna can have its own mobility
submodule, thus its own position and orientation, which also affects
reception.

The antenna module affects transmission and reception in multiple ways.
For example: - Its position and orientation is used when calculating
reception signal strength. By default, the antenna uses the containing
network node's mobility submodule to describe its position and
orientation, i.e. it has the same position and orientation as the
network node. However, antenna modules have optional mobility submodules
of their own. - The antenna applies a gain to the signal, which is taken
into account when calculating transmission and reception. The applied
gain depends on the antenna module's directional characteristics.



.. <!-- - the success depends on the signal power at the antenna
   - actually, the receiver and transmitter uses the antennas position for receiving
   - but the antenna also sets the reception power, depending on the direction and the antenna characteristic -->



.. <!-- - actually, the

   what does the antenna do ? does it apply gain to the signal when trasmitting ? does it apply gain when receiving ? seems so

   "Applies a gain to the signal which is taken into account when calculating reception" -->



.. <!-- INET contains several antenna module types. -->

INET contains the following antenna module types:

-  **Isotropic**:
-  ``IsotropicAntenna``: hypothetical antenna that radiates with the
   same intensity in all directions
-  ``ConstantGainAntenna``: the same as ``IsotropicAntenna``, but has a
   constant gain parameter
-  **Omnidirectional**:
-  ``DipoleAntenna``: models a dipole antenna
-  **Directional**:
-  ``ParabolicAntenna``: models a parabolic antenna's main radiation
   lobe
-  ``CosineAntenna``: models directional antenna characteristics with a
   cosine pattern
-  **Other**:
-  ``InterpolatingAntenna``: can model many complex antenna
   characteristics using linear interpolation

The default antenna module in all radios is ``IsotropicAntenna``.

Visualizing antenna directionality
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It is often useful to visualize antenna directional characteristics. The
``RadioVisualizer`` module can visualize this, using its antenna lobe
visualization feature. The visualizer can display the antenna's
radiation pattern, and the antenna lobes, i.e. the directions in which
the antenna's gain is stronger. For example, the radiation patterns of
an isotropic and a diretional antenna:

.. figure:: antennalobe2.png
   :width: 100%

The visualization of the radiation pattern depends on the viewing angle.
TODO

This visualization feature can be enabled by setting the visualizer's
``displayAntennaLobes`` parameter to ``true`` (false by default).



.. <!-- TODO about viewing angles -->

The model
---------

The showcase contains five example simulations, which demonstrate the
directional characteristics of five antenna modules. The simulation uses
the ``AntennaDirectionShowcase`` network:

.. figure:: network.png
   :width: 100%



.. <!--The playground size is 600x400 meters. <- it doesnt matter-->

The network contains two ``AdhocHost``\ s, named ``source`` and
``destination``. There is also an ``Ipv4NetworkConfigurator``, an
``IntegratedVisualizer``, and an ``Ieee80211ScalarRadioMedium`` module.

The source host is positioned in the center of the playground. The
destination host is configured to circle the source host, while the
source host pings the destination every 0.5 seconds. We'll use the ping
transmissions to probe the directional characteristics of ``source``'s
antenna, by recording the power of the received signal in
``destination``. The destination host will do one full circle around the
source. The distance of the two hosts will be constant to get meaningful
data about the antenna characteristics. We'll run the simulation with
five antenna types in ``source``: ``IsotropicAntenna``,
``ParabolicAntenna``, ``DipoleAntenna``, ``CosineAntenna``, and
``InterpolatingAntenna``. The destination has the default
``IsotropicAntenna`` in all simulations.



.. <!-- the goal is to get the directional characteristic, so the host goes around the other, and send probing transmission from each direction. we record the reception power. the distance stays the same, so its not dependent on that...the host does 1 lap, and in the result, the time maps to degrees. -->

The configurations for the five simulations differ in the antenna
settings, most of the settings are in the ``General`` configuration
section:



.. <p><pre class="include" src="omnetpp.ini" from="General" upto="displayLinks"></pre></p>

.. literalinclude:: ../omnetpp.ini
   :start-at: General
   :end-at: displayLink

The source host is configured to send ping requests every 0.5s. This is
effectively the probe interval, the antenna characteristic data can be
made more fine-grained by setting a more frequent ping rate. The
destination is configured to circle the source with a radius of 150m.
The simulation runs for 360s, and the speed of ``destination`` is set so
it does one full circle. This way, when plotting the reception power,
the time can be directly mapped to the direction angle.

.. todo::

   TODO: about the angle time mapping -> degrees is actually 90

The visualizer is set to display antenna lobes in ``source`` (the
``displayRadios`` is the master switch in ``RadioVisualizer``, so it
needs to be set to ``true``), signal arrivals (for the reception power
indication), and active data links (indicating successfully received
transmissions).

The antenna specific settings are defined in distinct configurations,
named according to the antenna type used (``IsotropicAntenna``,
``ParabolicAntenna``, ``DipoleAntenna``, ``CosineAntenna``, and
``InterpolatingAntenna``).

``IsotropicAntenna``
~~~~~~~~~~~~~~~~~~~~

The ``IsotropicAntenna`` is the default in all radio modules. This
module models a hypothetical antenna which radiates with the same power
in all directions. It is useful if the emphasis of the simulation is not
no on the details of antennas. This module can be used to approximate
real world directionless antennas. The module has no parameters. The
configuration for this antenna is ``IsotropicAntenna`` in omnetpp.ini.
The configuration just sets the antenna type in ``source``:



.. <p><pre class="include" src="omnetpp.ini" from="IsotropicAntenna" until="ParabolicAntenna"></pre></p>

.. literalinclude:: ../omnetpp.ini
   :start-at: IsotropicAntenna
   :end-before: ParabolicAntenna

When the simulation is run, it looks like the following:

.. figure:: isotropic1.png
   :width: 100%

The radiation pattern is a circle, as the antenna is directionless
(actually, the isotropic antenna's radiation pattern is a circle from
any viewpoint). Here is a video of the simulation running:



   .. video:: isotropic3.mp4



.. <!--internal video recording, animation speed 1, playback speed 21.88, normal run, crop 25 25 150 750-->

The destination node circles the source node, all ping messages are
successfully received.

.. figure:: isotropicchart.png
   :width: 100%

``ParabolicAntenna``
~~~~~~~~~~~~~~~~~~~~

The ``ParabolicAntenna`` module simulates the main lobe radiation
pattern of a parabolic antenna. The antenna module has the following
parameters:

-  ``MaxGain``: the maximum gain of the antenna
-  ``MinGain``: the minimum gain of the antenna
-  ``BeamWidth``: the 3 dB beam width

The configuration for this antenna is ``ParabolicAntenna`` in
omnetpp.ini:



.. <p><pre class="include" src="omnetpp.ini" from="ParabolicAntenna" until="DipoleAntenna"></pre></p>

.. literalinclude:: ../omnetpp.ini
   :start-at: ParabolicAntenna
   :end-before: DipoleAntenna

When the simulation is run, it looks like the following:

.. figure:: parabolic1.png
   :width: 100%

The radiation pattern is a narrow lobe. Note that in directions off from
the main direction, the radiation pattern might appear to be zero, but
actually, it is just very small. Note the small protrusion to the left
on the following, zoomed-in image:

.. figure:: parabolicsidelobe.png
   :width: 100%

Here is a video of the simulation:



   .. video:: parabolic3.mp4



.. <!--internal video recording, animation speed 1, playback speed 21.88, normal run, crop 25 25 150 750-->

The ping probe messages are successfully received when the destination
node is near the main lobe of ``source``'s antenna.

.. figure:: parabolicchart.png
   :width: 100%

``DipoleAntenna``
~~~~~~~~~~~~~~~~~

The ``DipoleAntenna`` module models a dipole antenna. It has one
parameter, ``length``. The configuration in omnetpp.ini is the
following:



.. <p><pre class="include" src="omnetpp.ini" from="DipoleAntenna" until="CosineAntenna"></pre></p>

.. literalinclude:: ../omnetpp.ini
   :start-at: DipoleAntenna
   :end-before: CosineAntenna

The configuration sets the antenna type to ``DipoleAntenna``, and the
antenna length to 0.1m. The elevation and bank parameters are used to
rotate the source node, so that the radiation pattern is more
interesting from the point of view of the simulation (the dipole
radiation pattern's donut shape is the same as the isotropic antenna's
when viewed from above).

TODO config



.. <p><pre class="include" src="omnetpp.ini" from="DipoleAntenna" until="InterpolatingAntenna"></pre></p>

.. literalinclude:: ../omnetpp.ini
   :start-at: DipoleAntenna
   :end-before: InterpolatingAntenna

It looks like this when the simulation is run:

.. figure:: dipole1.png
   :width: 100%

The radiation pattern is the dipole's donut shape, when viewed from the
side. Here is a video of the simulation:



   .. video:: dipole2.mp4



.. <!--internal video recording, animation speed 1, playback speed 21.88, normal run, crop 25 25 150 750-->

There is no successfull communication when the destination node is at
the null direction.

TODO: the visualization pattern...is that the gain at a given direction
is proportional to the line connecting the edge of the lobe shape and
the node ?

.. figure:: dipolechart.png
   :width: 100%

``CosineAntenna``
~~~~~~~~~~~~~~~~~

The ``CosineAntenna`` module approximates a directional antenna with a
cosine pattern. In this model, the shape of the radiation pattern is
given by a cosine exponent. The module has two parameters, ``MaxGain``
and ``Beamwidth``.

The radiation pattern is similar to the parabolic antenna's. It looks
like the following:

.. figure:: cosine1.png
   :width: 100%

Here is a video of the simulation:



   .. video:: cosine2.mp4

.. figure:: cosinechart.png
   :width: 100%

``InterpolatingAntenna``
~~~~~~~~~~~~~~~~~~~~~~~~

The ``InterpolatingAntenna`` module can model complex antenna
characteristics with linear interpolation. It has three parameters:
``HeadingGains``, ``ElevationGains`` and ``BankGains``. The parameters
take a sequence of gain and angle pairs (given in decibels and degrees),
the first pair must be ``0 0``. The characteristic at the intermediate
angles are calculated using linear interpolation. The gains can be
specified independently for the three Euler angles. The default for all
three parameters is ``"0 0"``, thus by default the antenna models an
isotropic antenna.

The configuration for this antenna is ``InterpolatingAntenna`` in
omnetpp.ini:



.. <p><pre class="include" src="omnetpp.ini" from="InterpolatingAntenna"></pre></p>

.. literalinclude:: ../omnetpp.ini
   :start-at: InterpolatingAntenna

The antenna type in ``source``'s radio is set to
``InterpolatingAntenna``. Only the heading gains are set, specifying a
hypothetical rectangular radiation pattern. It looks like the following:

.. figure:: interpolating1.png
   :width: 100%

TODO: insert the charts here as well ?



   .. video:: interpolating2.mp4

The edges of the rectangular radiation pattern can be made less rounded
by specifying more points in the gain parameter (the points are given by
the 1/cos(x) equation). TODO: not sure the last part is needed

.. figure:: interpolatingchart.png
   :width: 100%

TODO: not sure the individual characteristics are needed

.. figure:: allantennas.png
   :width: 100%
