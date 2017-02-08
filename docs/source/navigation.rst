Navigation
==========

.. NOTE:: The Turtlebot3 has been tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Navigation will use the map created in SLAM. The main purpose is to arrive at the user-defined goal position from the current robot position.

Bringup the TurtleBot3
----------------------

Now, we try to bring up the TurtleBot. Enter the following line in a terminal on the TurtleBot's SBC:

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_lds.launch
  stty -F /dev/ttyACM0

On the PC, run the navigation launch file
-----------------------------------------

.. code-block:: bash

  export TURTLEBOT3_MODEL=basic
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch

On the PC, launch rviz with the following command
-------------------------------------------------

.. code-block:: bash

  rosrun rviz rviz -d `rospack find turtlebot3_navigation`/rviz/turtlebot3_nav.rviz

Localize the TurtleBot
----------------------

When starting up, the TurtleBot does not know where it is. To provide him its approximate location on the map:

- Click the ``2D Pose Estimate`` button
- Click on the map where the TurtleBot approximately is and drag in the direction the TurtleBot is pointing.

You will see a collection of arrows which are hypotheses of the position of the TurtleBot. The laser scan should line up approximately with the walls in the map. If things don't line up well you can repeat the procedure.

Send a navigation goal
----------------------

With the TurtleBot localized, it can then autonomously plan through the environment.

To send a goal:

- Click the ``2D Nav Goal`` button
- Click on the map where you want the TurtleBot to drive and drag in the direction the TurtleBot should be pointing at the end.

This can fail if the path or goal is blocked.
If you want to stop the robot before it reaches it's goal, send it a goal at it's current location.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/o4yjNPKj3ps" frameborder="0" allowfullscreen></iframe>

Reference doc: http://wiki.ros.org/turtlebot_navigation/Tutorials/Autonomously%20navigate%20in%20a%20known%20map
