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

In this section, Alternative Ubuntu Desktop 16.04 LTS will be installed on Intel® Joule™ by following below instructions.

[``Remote PC``] Download the Ubuntu image ``Alternative Ubuntu 16.04 for Intel® Joule™`` from the link.

- http://people.canonical.com/~platform/snappy/tuchuck/desktop-final/tuchuck-xenial-desktop-iso-20170317-0.iso

[``Remote PC``] To make a bootable installation USB drive, you can use _`Alternative install(Ubuntu Desktop 16.04 LTS)`_ section from below link.

- https://developer.ubuntu.com/core/get-started/intel-joule

[``Remote PC``] Before installing Ubuntu, Joule needs a BIOS update to install Ubuntu Image. Download firmware which contains Joule's new BIOS and flash the BIOS into the Joule by following linked instructions below.

- https://software.intel.com/en-us/flashing-the-bios-on-joule

.. WARNING:: ``Intel® Joule™`` comes with ``passive heatsink`` in the package. It is recommended to use the heatsink. In order to use Joule without the heatsink, please follow the extra instruction: https://software.intel.com/en-us/node/721471

[``Intel® Joule™``] Connect ``micro HDMI to HDMI cable``, ``power connector supplied by OpenCR``, ``USB devices`` including ``Bootable USB drive``, ``mouse`` and ``keyboard``. You might need a USB hub to plug multiple USB devices.

[``Intel® Joule™``] Installation will be proceeded as shown in below images. When Joule is turned on, monitor will blink about 3 times after 5 seconds, and display options. Press ``f7`` to go to ``boot manager``.

.. image:: _static/preparation/j1.JPG

[``Intel® Joule™``] Select ``USB Device``.

.. image:: _static/preparation/j2.JPG

.. image:: _static/preparation/j3.JPG

.. image:: _static/preparation/j4.JPG

.. image:: _static/preparation/j5.JPG

[``Intel® Joule™``] Select ``Erase disk and install Ubuntu`` then ``continue``.

.. image:: _static/preparation/j6.JPG

[``Intel® Joule™``] Every ``Intel® Joule™`` has two different disk drives: 16GB micro SD Card and 16GB eMMC. This description suggest to install the ``Alternarive Ubuntu for Joule`` on the ``16GB eMMC``. Select ``MMC/SD card #2 (mmcblk1) - 15.7 GB MMC 016G32`` then ``continue``.

.. image:: _static/preparation/j7.JPG

.. image:: _static/preparation/j8.JPG

[``Intel® Joule™``] The installation will take about 10 minutes.

.. image:: _static/preparation/j9.JPG

[``Intel® Joule™``] When installation is completed, click ``Restart Now``.

.. image:: _static/preparation/j10.JPG

[``Intel® Joule™``] Remove bootable USB drive.

.. image:: _static/preparation/j11.JPG

[``Intel® Joule™``] Don't press any key. It will boot with ``16GB eMMC`` as a default boot device.

.. image:: _static/preparation/j12.JPG

.. image:: _static/preparation/j13.JPG

.. image:: _static/preparation/j14.JPG

[``Intel® Joule™``] Finish the rest of settings.

.. image:: _static/preparation/j15.JPG

.. image:: _static/preparation/j16.JPG

.. image:: _static/preparation/j17.JPG

.. image:: _static/preparation/j18.JPG

.. image:: _static/preparation/j19.JPG

.. image:: _static/preparation/j20.JPG

.. image:: _static/preparation/j21.JPG




Install ROS and packages (Burger and Waffle)
------------------------------------------------

.. WARNING:: The following contents correspond to ``TurtleBot``'s SBC (your Raspberry Pi or Intel® Joule™) which TurtleBot's main computer. You should never apply the following to your Remote PC (your desktop PC or laptop).

.. NOTE:: It takes about 2 hours to install the following ROS and TurtleBot3 related packages. This depends on your network environment.

.. image:: _static/logo_ros.png
    :align: center
    :target: http://wiki.ros.org

[``TurtleBot``] There are two ways to install `ROS`_. If you prefer manual installation, please take the second method.

**First Method** : Install the `ROS`_ by using a simple installation script file.

.. TIP:: The terminal application can be searched with the Ubuntu search icon on top left corner of screen. Shortcut key for terminal is Ctrl-Alt-T.

.. code-block:: bash

  sudo apt-get update
  sudo apt-get upgrade
  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh && chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

**Second Method** : You can start from "`1.2 Setup your sources.list`_" and keep working on until "`1.7 Getting rosinstall`_" from below ROS installation instruction link.

- http://wiki.ros.org/kinetic/Installation/Ubuntu

.. NOTE:: In order to check which packages are installed, please follow this link. https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh

[``TurtleBot``] The next step is to install dependent packages for the TurtleBot3 control.

.. code-block:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view

.. code-block:: bash

  cd ~/catkin_ws/src
  git clone https://github.com/ROBOTIS-GIT/hls_lfcd_lds_driver.git
  git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
  cd ~/catkin_ws && catkin_make

If catkin_make is completed without any errors, the preparation for using TurtleBot3 will be finished.

USB settings (Burger and Waffle)
--------------------------------

[``TurtleBot``] The following allows the USB port to be used for the OpenCR board without root privileges.

.. code-block:: bash

  cd ~/catkin_ws/src/turtlebot3
  sudo cp ./99-turtlebot3-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules
  sudo udevadm trigger

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

.. _Alternative install(Ubuntu Desktop 16.04 LTS): https://developer.ubuntu.com/core/get-started/intel-joule#alternative-install:-ubuntu-desktop-16.04-lts
.. _1.2 Setup your sources.list: http://wiki.ros.org/kinetic/Installation/Ubuntu#Installation.2BAC8-Ubuntu.2BAC8-Sources.Setup_your_sources.list
.. _1.7 Getting rosinstall : http://wiki.ros.org/kinetic/Installation/Ubuntu#Getting_rosinstall
.. _ROS: http://wiki.ros.org
