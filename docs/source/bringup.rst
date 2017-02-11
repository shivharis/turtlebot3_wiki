Bringup
=======

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Follow the instructions by focusing on which platform should carry out the commands. (for example, `TurtleBot3 SBC` or ` Remote PC`.

.. WARNING:: Check if the IP addresses on each devices are set correctly.

Bringup the TurtleBot3
----------------------

[Remote PC] Run ROScore.

.. code-block:: bash

  roscore


TurtleBot3 Basic
~~~~~~~~~~~~~~~~

[TurtleBot3 SBC] Give the LiDAR connected to ttyUSB0 socket the read/write permissions.

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0

[TurtleBot3 SBC] Bring up the basic packages to start the TurtleBot3 applications. 

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_lds.launch
  
.. NOTE:: 
  If the terminal shows `lost sync with device` error message, the sensor device of the TurtleBot3 must be incompletely connected. 
  
[TurtleBot3 SBC] (Temporary)

.. code-block:: bash

  stty -F /dev/ttyACM0

TurtleBot3 Premium
~~~~~~~~~~~~~~~~~~

[TurtleBot3 SBC] Give the LiDAR connected to ttyUSB0 socket the read/write permissions.

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  
[TurtleBot3 SBC] Bring up the basic packages to start the TurtleBot3 applications. 

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_r200.launch

.. NOTE:: 
  If the terminal shows `lost sync with device` error message, the sensor device of the TurtleBot3 must be incompletely connected. 
  
[TurtleBot3 SBC] (Temporary)

.. code-block:: bash

  stty -F /dev/ttyACM0

Control test with keyboard
-----------------------------

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
