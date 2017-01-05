SLAM
====

The SLAM is abbreviation of 'Simultaneous Localization and Mapping'. It refers to creating a map by estimating the current position in the space while searching the surrounding area while moving in arbitrary space.

We would like to introduce the video related to SLAM which is the basic function of TurtleBot3. Even if it is small size, low cost, we will do our best to SLAM and Navigation which is the basic function of Turtlebot brand.

.. youtube:: lkW4-dG2BCY

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/lkW4-dG2BCY" frameborder="0" allowfullscreen></iframe>

:Date: 2016.11.29
:Robot: TurtleBot3 basic model
:Sensor: Laser Distance Sensor
:ROS packages for SLAM: Gmapping / Cartographer
:Place: ROBOTIS Labs & HQ, 15th-floor corridor
:Duration: 55 minutes
:Total travel distance: 351 meters

1. Bringup the TurtleBot3
-------------------------

On the TurtleBot, start gmapping_demo on the turtlebot laptop.

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup.launch
  stty -F /dev/ttyACM0

Remote PC
---------

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_pc.launch
  roslaunch turtlebot3_slam turtlebot3_slam.launch
  rosrun rviz rviz -d `rospack find turtlebot3_slam`/rviz/turtlebot3_slam.rviz

.. code-block:: bash

  rosrun map_server map_saver

.. code-block:: bash
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch
  rosrun rviz rviz -d `rospack find turtlebot3_navigation`/rviz/turtlebot3_nav.rviz
