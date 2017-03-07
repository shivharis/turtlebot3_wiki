SLAM
====

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Make sure that the step **8.Bringup** was carried on previously to follow the instructions.

.. TIP:: Here recommends to use the joystick pad instead of the keyboard, because of its operability.

The Simultaneous Localization and Mapping, or SLAM, is a technique to draw a map by estimating the current position in virtual space while searching the areas in the arbitrary space.

The SLAM technique is a typical function of the TurtleBot3, and is a class of the Turtlebot brand. A video here shows how much accurately the TurtleBot3 can draw the map, even if it is a small, cheap robot platform.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/lkW4-dG2BCY" frameborder="0" allowfullscreen></iframe>


:Date: 2016.11.29
:Robot: TurtleBot3 BURGER model
:Sensor: Laser Distance Sensor
:Packages: Gmapping / Cartographer
:Place: ROBOTIS Labs & HQ, 15th-floor corridor
:Duration: 55 minutes
:Distance: Total 351 meters

Create a map through the teleoperation
------------------------------

[Remote PC] Open a terminal, then run the SLAM launch file.

.. code-block:: bash

  export TURTLEBOT3_MODEL=BURGER
  roslaunch turtlebot3_slam turtlebot3_slam.launch

[Remote PC] Visualize the model by the Rviz.

.. code-block:: bash

  rosrun rviz rviz -d `rospack find turtlebot3_slam`/rviz/turtlebot3_slam.rviz

Save the map to file
--------------------

[Remote PC] Open a terminal, then run map saver node.

.. code-block:: bash

  rosrun map_server map_saver -f ~/map

The files named as **map.pgm** and **map.yaml** will be built in the `~/` directory.
