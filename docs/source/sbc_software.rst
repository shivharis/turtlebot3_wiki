SBC Software Setup
==================

.. image:: _static/software/remote_pc_and_turtlebot.png
    :align: center

.. NOTE:: A ``SBC(Single-Board Computer)`` is a complete computer built on a single circuit board, with microprocessor(s), memory, input/output (I/O) and other features required of a functional computer. The TurtleBot3 uses Raspberry Pi (TB3 Burger) and Intel® Joule™ (TB3 Waffle) as SBC.

.. NOTE:: This instruction was tested on ``Ubuntu 16.04`` and ``ROS Kinetic Kame`` version.

Install the Linux for TurtleBot3 Burger (Raspberry Pi 3)
---------------------------------------------------------

.. WARNING:: The SDcard should have its capacity more than **8 GB** for the installation of the TurtleBot3.

[``Remote PC``] Download the ``Ubuntu MATE 16.04`` version on the Raspberry Pi 3 from the link below.

- https://ubuntu-mate.org/download/

.. image:: _static/preparation/download_ubuntu_mate_image.png

[``Remote PC``] To install Ubuntu MATE by using the image file, we recommend using GNOME Disks and the ``Restore Disk Image…`` option, which natively supports XZ compressed images.

.. code-block:: bash

  sudo apt-get install gnome-disk-utility

.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/V_6GNyL6Dac?ecver=1" frameborder="0" allowfullscreen></iframe>

|

.. TIP:: We recommend using ``GNOME Disks``, but we can use other methods using ``ddrescue`` on Linux

  .. code-block:: bash

    sudo apt-get install gddrescue xz-utils
    unxz ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img.xz
    sudo ddrescue -D --force ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img /dev/sdx

.. TIP:: We recommend using ``GNOME Disks``, but we can use other methods using ``Win32 Disk Imager`` on Windows

  https://sourceforge.net/projects/win32diskimager/

Install the Linux for TurtleBot3 Waffle (Intel® Joule™)
-------------------------------------------------------

[``Remote PC``] Download the image ``Ubuntu 16.04`` version in the Intel® Joule™ from the link below.

- https://developer.ubuntu.com/core/get-started/intel-joule#alternative-install:-ubuntu-desktop-16.04-lts

[``Remote PC``] Make a bootable USB drive to install Ubuntu.

- https://software.intel.com/en-us/node/705675#ubuntu

If necessary, see the other information in the link.

- https://software.intel.com/en-us/node/700692


Install the ROS and packages (Burger and Waffle)
------------------------------------------------

.. WARNING:: The following contents correspond to ``TurtleBot``'s SBC (your Raspberry Pi or Intel® Joule™) which TurtleBot's main computer. You should never apply the following to your Remote PC (your desktop or laptop PC).

.. NOTE:: It takes about 2 hours to install the following ROS and TurtleBot3 related packages. This depends on your network environment.

.. image:: _static/logo_ros.png
    :align: center
    :target: http://wiki.ros.org

[``TurtleBot``] Install the `ROS`_ by using a simple installation script file.

.. code-block:: bash

  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh && chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

or follow the typical instruction in the link.

- http://wiki.ros.org/kinetic/Installation/Ubuntu

[``TurtleBot``] The next step is to install the dependent packages for the TurtleBot3 control.

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-turtlebot-teleop ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view

.. code-block:: bash

  cd ~/catkin_ws/src
  git clone https://github.com/ROBOTIS-GIT/hls_lfcd_lds_driver.git
  git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
  cd ~/catkin_ws && catkin_make

If catkin_make is completed without any errors, the preparation for using TurtleBot3 will be finished.

.. WARNING:: When you are working in Raspberry Pi 3, you should delete ''turtlebot3_gazebo'' folder before catkin_make.

.. code-block:: bash

  cd ~/catkin_ws/src/turtlebot3
  sudo rm -r turtlebot3_gazebo

USB settings (Burger and Waffle)
--------------------------------

[``TurtleBot``] The following allows the USB port to be used for the OpenCR board without root privileges.

.. code-block:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules


Network Configuration (Burger and Waffle)
-----------------------------------------

.. image:: _static/software/network_configuration.png

ROS needs IP addresses to communicate between the TurtleBot and the remote PC.

[``TurtleBot``] Type the next to find out the IP address of your TurtleBot.

.. code-block:: bash

  ifconfig

Rectangled text is the IP address of the ``TurtleBot``.

[``TurtleBot``] Do the following.

.. code-block:: bash

  pluma ~/.bashrc

[``TurtleBot``] Change the `localhost` into the IP address shown as follows.

.. image:: _static/software/network_configuration4.png

[``TurtleBot``] Then, source the bashrc

.. code-block:: bash

  source ~/.bashrc

.. image:: _static/software/network_configuration5.png


.. _ROS: http://wiki.ros.org
