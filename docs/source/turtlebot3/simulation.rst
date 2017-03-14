Simulation
==========

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

TurtleBot3 fake node implementation
-----------------------------------

``TurtleBot3 fake node`` is a very simple simulation node that can be run without a real robot. You can move a robot through a teleop node on a virtual TurtleBot3 on RViz

.. code-block:: bash

  export TURTLEBOT3_MODEL=burger
  roslaunch turtlebot3_fake turtlebot3_fake.launch

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_teleop_key.launch

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/iHXZSLBJHMg" frameborder="0" allowfullscreen></iframe>

|

Stage (2D)
----------

(TODO)

Gazebo (3D)
-----------

(TODO)
