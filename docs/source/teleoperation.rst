Teleoperation
=============

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Make sure that **7.Bringup** was carried on previously to do as follows.

TurtleBot3 can be teleoperated by various devices. it is tested by using several wireless devices e.g. PS3, XBOX 360, ROBOTIS RC100, etc. These examples, except the LEAP Motion example, can be operated by ROS on Ubuntu mate 16.04 with Raspberry Pi 3 and OpenCR which controls the Dynamixel XM-430.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/Z4s18hlazb4" frameborder="0" allowfullscreen></iframe>

.. TIP:: The following instructions are useless when it is operated on the TurtleBot3's SBC.

Keyboard
--------

[Remote PC] Get the teleoperation package which uses the keyboard.

.. code-block:: bash

  sudo apt-get install ros-kinetic-teleop-twist-keyboard

.. NOTE:: Here recommends to follow the steps in the remote PC.

[Remote PC] Launch the file for simple teleoperation test.

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_teleop_key.launch

[Remote PC] If the file succeeds to be launched, the following will be appeared to the terminal.

.. code-block:: bash

  Control Your Turtlebot!
  ---------------------------
  Moving around:
     u    i    o
     j    k    l
     m    ,    .

  q/z : increase/decrease max speeds by 10%
  w/x : increase/decrease only linear speed by 10%
  e/c : increase/decrease only angular speed by 10%
  space key, k : force stop
  anything else : stop smoothly

  CTRL-C to quit

  currently:	speed 0.2	turn 1

.. WARNING:: Be careful when the test is being carried on a table.
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
