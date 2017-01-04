Teleoperation
=============

The TurtleBot3 would be teleoperated by various devices. We tested it using several wireless devices e.g. PS3, XBOX 360, ROBOTIS RC100, etc. This example is operated by ROS on Ubuntu mate 16.04 with Raspberry Pi 3 (except that it tested by LEAP Motion) and OpenCR which controlls Dynamixel XM-430.

.. youtube:: Z4s18hlazb4

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/Z4s18hlazb4" frameborder="0" allowfullscreen></iframe>

Preparation on SBC
------------------

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup.launch
  stty -F /dev/ttyACM0

Keyboard
--------

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_pc.launch
  roslaunch turtlebot_teleop keyboard_teleop.launch

RC100
-----

(TODO)

PS3 Joystick
------------

(TODO)

XBOX 360 Joystick
-----------------

(TODO)

Wii Remote
----------

(TODO)

Nunchuk
-------

(TODO)

Android App
-------

(TODO)

LEAP Motion
-------

(TODO)

Myo
---

(TODO)
