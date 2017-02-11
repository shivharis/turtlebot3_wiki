Bringup
=======

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Follow the instructions by focusing on which platform should carry out the commands, for example, `TurtleBot3 SBC` or ` Remote PC`.

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

Now, test the TurtleBot3 with various teleoperation methods.
