PC Software Setup
=================

.. NOTE:: We tested the Turtlebot 3 on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Install the Ubuntu for the remote PC (Desktop or Laptop PC)
-----------------------------------------------------------

Download the ``Ubuntu 16.04.1`` version for desktop PC from the address below.

- https://www.ubuntu.com/download/desktop

If you need some help installing Ubuntu, please check out step-by-step guide below.

- https://www.ubuntu.com/download/desktop/install-ubuntu-desktop

Install the ROS and packages
----------------------------

.. image:: _static/logo_ros.png
    :align: center
    :target: http://wiki.ros.org

Install the `ROS`_ using simple script file below.

.. code-block:: bash

  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh && chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

or you can use the typical instructions below.

- http://wiki.ros.org/kinetic/Installation/Ubuntu

The next step is to install the relevant package for TurtleBot3.

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-hls-lfcd-lds-driver ros-kinetic-urdf ros-kinetic-xacro

.. code-block:: bash

  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
  cd ~/catkin_ws && catkin_make

If catkin_make completes successfully without any errors, you have completed the preparation to use TurtlebBot3.


Network Configuration
---------------------

.. image:: _static/software/network_configuration.png

.. _ROS: http://wiki.ros.org
