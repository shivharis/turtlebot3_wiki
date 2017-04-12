.. _chapter_bringup:

Bringup
=======

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Follow the instructions and do at the TurtleBot3 SBC.

.. WARNING:: Check if the IP addresses on each devices are set correctly.

Bringup the TurtleBot3
----------------------

[Remote PC] Run roscore.

.. code-block:: bash

  roscore


TurtleBot3 BURGER
~~~~~~~~~~~~~~~~~

[TurtleBot3 SBC] Give the LiDAR connected to ttyUSB0 socket the read/write permissions.

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0

[TurtleBot3 SBC] Bring up the basic packages to start the TurtleBot3 applications.

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_robot.launch

.. NOTE::
  If the terminal shows `lost sync with device` error message, the sensor device of the TurtleBot3 must be incompletely connected.


TurtleBot3 WAFFLE
~~~~~~~~~~~~~~~~~

[TurtleBot3 SBC] Give the LiDAR connected to ttyUSB0 socket the read/write permissions.

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0

[TurtleBot3 SBC] Bring up the basic packages to start the TurtleBot3 applications.

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_robot.launch

.. NOTE::
  If the terminal shows `lost sync with device` error message, the sensor device of the TurtleBot3 must be incompletely connected.

Now, test the TurtleBot3 with various teleoperation methods.
