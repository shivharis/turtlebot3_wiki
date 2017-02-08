Bringup
=======

.. NOTE:: The Turtlebot3 has been tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Bringup the TurtleBot3
----------------------

TurtleBot3 Basic
~~~~~~~~~~~~~~~~

Give the LiDAR connected to ttyUSB0 socket the read/write permissions.

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0

Bring up the basic packages to start the TurtleBot3 applications. 

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_lds.launch
  


.. code-block:: bash
  stty -F /dev/ttyACM0

TurtleBot3 Premium
~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  
Bring up the basic packages to start the TurtleBot3 applications. 

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_r200.launch



.. code-block:: bash

  stty -F /dev/ttyACM0

Control test with keyboard
-----------------------------

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_teleop_key.launch

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

.. WARNING:: If you are testing a turtle bot on a table, you should be careful of falling accidents.
