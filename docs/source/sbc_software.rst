SBC Software Setup
==================

.. NOTE:: We tested the Turtlebot 3 on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Install the Ubuntu MATE for the Raspberry Pi 3 (TurtleBot3 Basic Model)
-----------------------------------------------------------------------

Download the disk image file for raspberry Pi 3 from the address below. This disk image file contains ``Ubuntu MATE 16.04.1`` and ``ROS kinetic kame``. In addition, all the ROS packages needed for TurtleBot Basic are included.

- https://goo.gl/rdum6W

Making a microSDHC: We recommend using GNOME Disks and the ``Restore Disk Image…`` option, which natively supports XZ compressed images. First, insert the microSD card into your remote PC (ubuntu) and restore the disk image as shown below.

.. code-block:: bash

  gnome-disks

.. image:: _static/software/rpi_disk1.png
   :width: 300px

.. image:: _static/software/rpi_disk2.png
   :width: 300px

.. image:: _static/software/rpi_disk3.png
   :width: 300px

.. image:: _static/software/rpi_disk4.png
   :width: 300px

.. image:: _static/software/rpi_disk5.png
   :width: 300px

.. image:: _static/software/rpi_disk6.png
   :width: 300px

Install the Ubuntu for the Intel Joule (TurtleBot3 Premium Model)
-----------------------------------------------------------------

(TODO)

Network Configuration
---------------------

.. image:: _static/software/network_configuration.png

Manual setting (Ubuntu and ROS)
-------------------------------

.. WARNING:: If you have used the Rasberry PI image provided by ROBOTIS, the ROS and packages described below have already been installed and so you do not need to run the following.

[Manual] Install the Ubuntu MATE for the Raspberry Pi 3 (TurtleBot3 Basic Model)
--------------------------------------------------------------------------------

Download the ``Ubuntu MATE 16.04.1`` version for raspberry Pi 3 from the address below.

- https://ubuntu-mate.org/download/

.. image:: _static/preparation/download_ubuntu_mate_image.png

To install Ubuntu MATE using the downloaded image file, please refer to the link below.

- https://ubuntu-mate.org/raspberry-pi/

[Manual] Install the Ubuntu for the Intel Joule (TurtleBot3 Premium Model)
--------------------------------------------------------------------------

Download the image ``Ubuntu 16.04`` version for Intel Joule from the address below.

- https://developer.ubuntu.com/core/get-started/intel-joule#alternative-install:-ubuntu-desktop-16.04-lts

Creating a bootable USB drive to install Ubuntu.

- https://software.intel.com/en-us/node/705675#ubuntu

Other information

- https://software.intel.com/en-us/node/700692

[Manual] Install the ROS and packages
-------------------------------------

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

[Manual] USB settings
---------------------

Allows the OpenCR USB port to be used on TurtleBot3 without root privileges.

.. code-block:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

.. _ROS: http://wiki.ros.org
