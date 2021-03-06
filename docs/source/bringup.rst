.. _chapter_bringup:

Bringup
=======

.. image:: _static/software/remote_pc_and_turtlebot.png
    :align: center

.. NOTE:: This instruction was tested on ``Ubuntu 16.04`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Follow the instructions and do at your ``TurtleBot`` without roscore command.

.. WARNING:: Check if the IP addresses on each devices are set correctly.

.. WARNING:: The buzzer alarm is continuously sounded and the robot's actuator operation is stopped when the battery of the robot reaches 11V. The battery must be charged when the buzzer alarm sounds.


Bringup the TurtleBot3
----------------------

.. TIP:: Terminal is opened to go to the Ubuntu search icon, type "Terminal" or use Ctrl-Alt-T.

[``Remote PC``] Run roscore.

.. code-block:: bash

  roscore


TurtleBot3 Burger
~~~~~~~~~~~~~~~~~

[``TurtleBot``] Bring up the basic packages to start the TurtleBot3 applications.

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_robot.launch

.. TIP::
  Someone who want to launch Lidar sensor or core separately, use below command

  .. code-block:: bash

    roslaunch turtlebot3_bringup turtlebot3_lidar.launch
    roslaunch turtlebot3_bringup turtlebot3_core.launch

.. NOTE::
  If the terminal shows `lost sync with device` error message, the sensor device of the TurtleBot3 must be incompletely connected.

[``Remote PC``] Run rviz

.. code-block:: bash

  export TURTLEBOT3_MODEL=burger
  roslaunch turtlebot3_bringup turtlebot3_model.launch

.. image:: _static/bringup/rviz_burger_model.jpg

TurtleBot3 Waffle
~~~~~~~~~~~~~~~~~

[``TurtleBot``] Bring up the basic packages to start the TurtleBot3 applications.

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_robot.launch

.. TIP::
  Someone who want to launch Lidar sensor, Intel® RealSense™ R200 or core separately, use below command

  .. code-block:: bash

    roslaunch turtlebot3_bringup turtlebot3_lidar.launch
    roslaunch turtlebot3_bringup turtlebot3_realsense.launch
    roslaunch turtlebot3_bringup turtlebot3_core.launch

.. NOTE::
  If the terminal shows `lost sync with device` error message, the sensor device of the TurtleBot3 must be incompletely connected.

[``Remote PC``] Run rviz

.. code-block:: bash

  export TURTLEBOT3_MODEL=waffle
  roslaunch turtlebot3_bringup turtlebot3_model.launch

.. image:: _static/bringup/rviz_waffle_model.jpg

Now, test the TurtleBot3 with various teleoperation methods.
