Appendix #LDS
==============

.. image:: _static/appendix/lds/lds.png

Overview
--------

HLS-LFCD LDS is used for both models of the TurtleBot3. The LDS(Laser Distance Sensor) is a sensor which sends the data, gathered by the obstacle detection, to the host for the Simultaneous Localization and Mapping (SLAM) technique.

Specification
-------------

Basic performance specification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+--------------------------+--------------------------------------------------------------------+
| Items                    | Specifications                                                     |
+==========================+====================================================================+
| Operating supply voltage | 5V DC ±5%                                                          |
+--------------------------+--------------------------------------------------------------------+
| Light source             | Semiconductor Laser Diode(λ=785nm)                                 |
+--------------------------+--------------------------------------------------------------------+
| Laser safety             | IEC60825-1 Class 1                                                 |
+--------------------------+--------------------------------------------------------------------+
| Current consumption      | 400mA or less (Rush current 1A)                                    |
+--------------------------+--------------------------------------------------------------------+
| Detection distance       | 120mm ~ 3,500mm                                                    |
+--------------------------+--------------------------------------------------------------------+
| Interface                | 3.3V USART (230,400 bps) 42bytes per 6 degrees, Full Duplex option |
+--------------------------+--------------------------------------------------------------------+
| Ambient Light Resistance | 10,000 lux or less                                                 |
+--------------------------+--------------------------------------------------------------------+
| Sampling Rate            | 1.8kHz                                                             |
+--------------------------+--------------------------------------------------------------------+
| Dimensions               | 69.5(W) X 95.5(D) X 39.5(H)mm                                      |
+--------------------------+--------------------------------------------------------------------+
| Mass                     | Under 125g                                                         |
+--------------------------+--------------------------------------------------------------------+

Measurement performance specification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------------------------------+---------------+
| Items                              | Specifications|
+====================================+===============+
| Distance Range                     | 120 ~ 3,500mm |
+------------------------------------+---------------+
| Distance Accuracy (120mm ~ 499mm)  | ±15mm         |
+------------------------------------+---------------+
| Distance Accuracy(500mm ~ 3,500mm) | ±5.0%         |
+------------------------------------+---------------+
| Distance Precision(120mm ~ 499mm)  | ±10mm         |
+------------------------------------+---------------+
| Distance Precision(500mm ~ 3,500mm)| ±3.5%         |
+------------------------------------+---------------+
| Scan Rate                          | 300±10 rpm    |
+------------------------------------+---------------+
| Angular Range                      | 360°          |
+------------------------------------+---------------+
| Angular Resolution                 | 1°            |
+------------------------------------+---------------+

Detail specification document
-----------------------------

The following includes the contents, like a basic performance, measurement performance, mechanism layout, optical path, data information, pin description, commands.

here is the detail specification document :download:`pdf <_static/doc/LDS_Basic_Specification.pdf>`


LDS for the TurtleBot3
-----------------

The HLS-LFCD LDS is used for the TurtleBot3 BURGER and TurtleBot3 WAFFLE.

.. image:: _static/hardware/turtlebot3_models.png

Introduction Video
------------------

ROS Hector SLAM demo using only a HLS-LFCD LDS made by HLDS (Hitachi-LG Data Storage).

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/s7CflpA6TOo" frameborder="0" allowfullscreen></iframe>

|

ROS Gmapping and Cartographer SLAM demo using TurtleBot3 and the HLS-LFCD LDS.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/lkW4-dG2BCY" frameborder="0" allowfullscreen></iframe>

|

User's guide
------------

We are offering the `ROS package for LSD`_. The hls_lfcd_lds_driver package is a driver for "HLS(Hitachi-LG Sensor) LFCD LDS(Laser Distance Sensor)".

Installation
~~~~~~~

.. code-block:: bash

  sudo apt-get install ros-kinetic-hls-lfcd-lds-driver

Setting the permission for the HLS-LFCD LDS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0

Run hlds_laser_publisher node
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  roslaunch hls_lfcd_lds_driver hlds_laser.launch

Run hlds_laser_publisher node with RViz
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  roslaunch hls_lfcd_lds_driver view_hlds_laser.launch

.. _ROS package for LSD: http://wiki.ros.org/hls_lfcd_lds_driver
