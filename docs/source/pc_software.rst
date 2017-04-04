PC Software Setup
=================

.. NOTE:: This instruction was tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Install the Ubuntu in the remote PC (Desktop or Laptop PC)
-----------------------------------------------------------

Download the ``Ubuntu 16.04.1`` version on the remote PC from the following link.

- https://www.ubuntu.com/download/desktop

If it needs some help to install Ubuntu, check out the step-by-step guide.

- https://www.ubuntu.com/download/desktop/install-ubuntu-desktop

Install the ROS
---------------

.. image:: _static/logo_ros.png
    :align: center
    :target: http://wiki.ros.org

Install the `ROS`_ by using a simple installation script file

.. code-block:: bash

  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh && chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

or follow the typical instruction in the link.

- http://wiki.ros.org/kinetic/Installation/Ubuntu

Install the dependent packages
------------------------------

The next step is to install the dependent packages for the TurtleBot3 control.

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-hls-lfcd-lds-driver ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-gmapping ros-kinetic-turtlebot-teleop

.. code-block:: bash

  cd ~/catkin_ws/src/
  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
  cd ~/catkin_ws && catkin_make

If catkin_make is completed without any errors, the preparation for using TurtleBot3 will be finished.


Network Configuration
---------------------

.. image:: _static/software/network_configuration.png

ROS needs IP addresses to communicate between the turtlebot and the remote PC.

Type the next to find out IP address.

.. code-block:: bash

  ifconfig

Rectangled text is the IP address of the remote PC.

Do the following.

.. code-block:: bash

  gedit ~/.bashrc

Change the `localhost` into the IP address shown as follows.

.. image:: _static/software/network_configuration2.png

Then, source the bashrc

.. code-block:: bash

  source ~/.bashrc

.. image:: _static/software/network_configuration3.png


.. _ROS: http://wiki.ros.org
