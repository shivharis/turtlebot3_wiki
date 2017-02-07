Teleoperation
=============

The TurtleBot3 would be teleoperated by various devices. We tested it using several wireless devices e.g. PS3, XBOX 360, ROBOTIS RC100, etc. This example is operated by ROS on Ubuntu mate 16.04 with Raspberry Pi 3 (except that it tested by LEAP Motion) and OpenCR which controlls Dynamixel XM-430.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/Z4s18hlazb4" frameborder="0" allowfullscreen></iframe>

|

Bringup the TurtleBot3
----------------------

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup.launch
  stty -F /dev/ttyACM0

.. NOTE:: The following instructions are for remotely controlling the TurtleBot3. Therefore, it should be run on the user's remote PC, not the TurtleBot3's SBC.

Keyboard
--------

.. code-block:: bash

  sudo apt-get install ros-kinetic-teleop-twist-keyboard

.. code-block:: bash

  rosrun teleop_twist_keyboard teleop_twist_keyboard.py

RC100
-----

When using RC100 of ROBOTIS, it is used directly with OpenCR, so no other package is required.

PS3 Joystick
------------

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-joy

.. code-block:: bash

  roslaunch teleop_twist_joy teleop.launch

XBOX 360 Joystick
-----------------

.. code-block:: bash

  sudo apt-get install xboxdrv ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-joy

.. code-block:: bash

  xboxdrv --silent
  roslaunch teleop_twist_joy teleop.launch

Wii Remote
----------

.. code-block:: bash

  rosdep install wiimote
  rosmake wiimote

.. code-block:: bash

  rosrun wiimote wiimote_node.py
  rosrun learning_wiimote turtle_teleop_wiimote

Nunchuk
-------

(TODO)

Android App
-----------

Downloads the `ROS Teleop`_ and run this app.


LEAP Motion
-----------

- https://www.leapmotion.com/setup
- https://developer.leapmotion.com/downloads/sdk-preview

.. code-block:: bash

  leapd
  LeapCommandPanel
  git clone git@github.com:warp1337/rosleapmotion.git

.. code-block:: bash

  rosrun leap_motion sender.py

Myo
---

(TODO)

.. _ROS Teleop: https://play.google.com/store/apps/details?id=com.github.rosjava.android_apps.teleop.indigo
