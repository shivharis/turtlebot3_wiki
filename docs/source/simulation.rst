.. _chapter_simulation:

Simulation
==========

.. image:: _static/software/remote_pc_and_turtlebot.png
    :align: center

.. WARNING:: The following contents correspond to ``Remote PC`` (your desktop or laptop PC) which controls TurtleBot3. You should never apply the following to your TurtleBot.

.. NOTE:: This instruction was tested on ``Ubuntu 16.04`` and ``ROS Kinetic Kame`` version.

TurtleBot3 fake node implementation
-----------------------------------

.. TIP:: Terminal is opened to go to the Ubuntu search icon, type "Terminal" or use Ctrl-Alt-T.

Install the dependent packages for the TurtleBot3 Simulations.

.. code-block:: bash

  cd ~/catkin_ws/src/
  git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
  cd ~/catkin_ws && catkin_make

``TurtleBot3 fake node`` is a very simple simulation node that can be run without a real robot. You can move a robot through a teleop node on a virtual TurtleBot3 on RViz.

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

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/xXM5r_SVkWM" frameborder="0" allowfullscreen></iframe>

|

.. TIP:: Terminal is opened to go to the Ubuntu search icon, type "Terminal" or use Ctrl-Alt-T.

Before launch gazebo simulation with TurtleBot3, ``TurtleBot3 model files`` are moved to ``gazebo model folder``.

.. code-block:: bash

  cp -r  ~/catkin_ws/src/turtlebot3/turtlebot3_gazebo/worlds/turtlebot3 ~/.gazebo/models/

Set Turtlebot3 model. (burger or waffle)

.. code-block:: bash

  export TURTLEBOT3_MODEL=burger

``TurtleBot3 empty world`` is a basic gazebo enviroment except any objects.

.. code-block:: bash

  roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch

.. image:: _static/simulation/turtlebot3_empty_world.png

The TurtleBot3 drives by teleoperation with a keyboard.

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_teleop_key.launch

``TurtleBot3 world`` is a simple map has the shape of a TurtleBot3 symbol.
  
.. code-block:: bash

  roslaunch turtlebot3_gazebo turtlebot3_world.launch

.. image:: _static/simulation/turtlebot3_world_bugger.png

.. image:: _static/simulation/turtlebot3_world_waffle.png

The TurtleBot3 can freely moves in a turtlebot3 world.

.. code-block:: bash

  roslaunch turtlebot3_gazebo turtlebot3_simulation.launch

Rviz shows published topics when simulation is launched.

.. code-block:: bash

  roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch

.. image:: _static/simulation/turtlebot3_gazebo_rviz.png
