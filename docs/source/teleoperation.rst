.. _chapter_teleoperation:

Teleoperation
=============

.. image:: _static/software/remote_pc_and_turtlebot.png
    :align: center

.. NOTE:: This instruction was tested on ``Ubuntu 16.04`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Make sure that the step :ref:`[Bringup]<chapter_bringup>` was carried on previously to follow the instructions.

.. WARNING:: Be careful when the test is being carried on the table.

.. TIP:: The following instructions are useless when it is operated on the TurtleBot3's SBC. **Do this at your Remote PC**.

TurtleBot3 can be teleoperated by various devices. it is tested by using several wireless devices e.g. PS3, XBOX 360, ROBOTIS RC100, etc. These examples, except the LEAP Motion example, can be operated by ROS on Ubuntu mate 16.04 with Raspberry Pi 3 and OpenCR which controls the Dynamixel.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/Z4s18hlazb4" frameborder="0" allowfullscreen></iframe>

|

Keyboard
--------

.. TIP:: Terminal is opened to go to the Ubuntu search icon, type "Terminal" or use Ctrl-Alt-T.

[``Remote PC``] Launch the file for simple teleoperation test.

.. code-block:: bash

  roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

[``Remote PC``] If the file succeeds to be launched, the following will be appeared to the terminal.

.. code-block:: bash

  Control Your Turtlebot3!
  ---------------------------
  Moving around:
          w
     a    s    d
          x

  w/x : increase/decrease linear velocity
  a/d : increase/decrease angular velocity
  space key, s : force stop

  CTRL-C to quit

RC100
-----

The settings for using the ROBOTIS RC100 is already in the OpenCR firmware for ROS, so there are no more required packages.

PS3 Joystick
------------

[``Remote PC``] Connect the PS3 Joystick to the PC via the Bluetooth or the USB cable.

[``Remote PC``] Install the packages for the teleoperation using PS3 joystick.

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-joy

[``Remote PC``] Run the teleoperation package for the PS3 joystick.

.. code-block:: bash

  roslaunch teleop_twist_joy teleop.launch

XBOX 360 Joystick
-----------------

[``Remote PC``] Connect the XBOX 360 Joystick to the PC via the Wireless Adapter or the USB cable.

[``Remote PC``] Install the packages for the teleoperation using XBOX 360 joystick.

.. code-block:: bash

  sudo apt-get install xboxdrv ros-kinetic-joy ros-kinetic-joystick-drivers ros-kinetic-teleop-twist-joy


[``Remote PC``] Run the teleoperation package for the XBOX 360 joystick.

.. code-block:: bash

  xboxdrv --silent
  roslaunch teleop_twist_joy teleop.launch

Wii Remote
----------

[``Remote PC``] Connect the Wii remote to the PC via the Bluetooth.

[``Remote PC``] Install the packages for the teleoperation using Wii remote.

.. code-block:: bash

  rosdep install wiimote
  rosmake wiimote

[``Remote PC``] Run the teleoperation package for the Wii remote.

.. code-block:: bash

  rosrun wiimote wiimote_node.py
  rosrun learning_wiimote turtle_teleop_wiimote

Nunchuk
-------

(TODO)

Android App
-----------

Download the `ROS Teleop`_ and run the application program.


LEAP Motion
-----------

[``Remote PC``] Connect the LEAP motion to the PC via the Bluetooth.

[``Remote PC``] Install the packages for the teleoperation using LEAP motion.

- https://www.leapmotion.com/setup
- https://developer.leapmotion.com/downloads/sdk-preview

.. code-block:: bash

  leapd
  LeapCommandPanel
  git clone git@github.com:warp1337/rosleapmotion.git

[``Remote PC``] Run the teleoperation package for the LEAP motion.

.. code-block:: bash

  rosrun leap_motion sender.py

Myo
---

(TODO)

.. _ROS Teleop: https://play.google.com/store/apps/details?id=com.github.rosjava.android_apps.teleop.indigo
