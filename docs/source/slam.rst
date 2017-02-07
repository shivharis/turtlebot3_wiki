SLAM
====

The SLAM is abbreviation of 'Simultaneous Localization and Mapping'. It refers to creating a map by estimating the current position in the space while searching the surrounding area while moving in arbitrary space.

We would like to introduce the video related to SLAM which is the basic function of TurtleBot3. Even if it is small size, low cost, we will do our best to SLAM and Navigation which is the basic function of Turtlebot brand.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/lkW4-dG2BCY" frameborder="0" allowfullscreen></iframe>

|

:Date: 2016.11.29
:Robot: TurtleBot3 basic model
:Sensor: Laser Distance Sensor
:Packages: Gmapping / Cartographer
:Place: ROBOTIS Labs & HQ, 15th-floor corridor
:Duration: 55 minutes
:Distance: Total 351 meters

Bringup the TurtleBot3
----------------------

Now, we try to bring up the TurtleBot. Enter the following line in a terminal on the TurtleBot's SBC:

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_lds.launch
  stty -F /dev/ttyACM0

Create a map via teleoperation
------------------------------

On the remote PC, open a terminal window and run:

.. code-block:: bash

  export TURTLEBOT3_MODEL=basic
  roslaunch turtlebot3_slam turtlebot3_slam.launch

.. code-block:: bash

  rosrun rviz rviz -d `rospack find turtlebot3_slam`/rviz/turtlebot3_slam.rviz

.. NOTE:: Instead of using the keyboard, We recommend using a joystick that is better in operability.

Save the map to file
--------------------

On TurtleBot, open a terminal window and run:

.. code-block:: bash

  rosrun map_server map_saver -f ~/map

You will now see two files in the `~/` directory ``map.pgm`` and ``map.yaml``
