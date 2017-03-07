Navigation
==========

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

.. WARNING:: Make sure that the step **8.Bringup** was carried on previously to follow the instructions.

.. WARNING:: The navigation uses the map data created in the step **9.SLAM**. Check if the previous step is not done yet.

.. WARNING:: Be careful when the test is being carried on the table.

The main use of the navigation technique is to bring the robot into the expected position.


Do the navigation
-----------------------------------------

[Remote PC] Launch the navigation file.

.. code-block:: bash

  export TURTLEBOT3_MODEL=BURGER
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch

[Remote PC] Launch the Rviz.

.. code-block:: bash

  rosrun rviz rviz -d `rospack find turtlebot3_navigation`/rviz/turtlebot3_nav.rviz

[Remote PC] Before starting the navigation, the TurtleBot3 should know its location and pose. To give the initial data, follow the description.

- Click the ``2D Pose Estimate`` button.
- Set the approximate location on the map by clicking and drag the direction accros the map.

Each points of arrow mean the expected poses of the TurtleBot3. The laser scanner will draw the lines at approximate positions like the wall on the map. If the drawing doesn't show the lines well, repeat above procedures.

[Remote PC] When the TurtleBot3 is localized, it will automatically plan the path. To send a goal location,

- Click the ``2D Nav Goal`` button.
- Click on the map where you want the TurtleBot to drive and drag in the direction the TurtleBot should be pointing at the end.

This can be failed if the path for the goal location is blocked.
To stop the robot before it reaches to the goal location, send the current location of the TurtleBot3.

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/o4yjNPKj3ps" frameborder="0" allowfullscreen></iframe>

Reference doc: http://wiki.ros.org/turtlebot_navigation/Tutorials/Autonomously%20navigate%20in%20a%20known%20map
