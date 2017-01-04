Bringup
=======

SBC
---

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup.launch
  stty -F /dev/ttyACM0

PC
--

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_pc.launch
  roslaunch turtlebot3_slam turtlebot3_slam.launch
  rosrun rviz rviz -d `rospack find turtlebot3_slam`/rviz/turtlebot3_slam.rviz

.. code-block:: bash

  rosrun map_server map_saver

.. code-block:: bash
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch
  rosrun rviz rviz -d `rospack find turtlebot3_navigation`/rviz/turtlebot3_nav.rviz
