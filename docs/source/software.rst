Software Setup
==============

.. NOTE:: We tested the Turtlebot 3 on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

Install the Ubuntu MATE for the Raspberry Pi 3 (TurtleBot3 Basic Model)
-----------------------------------------------------------------------

Download the ``Ubuntu MATE 16.04.1`` version for raspberry Pi 3 from the address below.

- https://ubuntu-mate.org/download/

.. image:: _static/preparation/download_ubuntu_mate_image.png

To install Ubuntu MATE using the downloaded image file, please refer to the link below.

- https://ubuntu-mate.org/raspberry-pi/

Install the Ubuntu for the Intel Joule (TurtleBot3 Premium Model)
-----------------------------------------------------------------

Download the ``Ubuntu 16.04.1`` version for Intel Joule from the address below.

- https://developer.ubuntu.com/en/snappy/start/intel-joule/

Creating a bootable USB drive to install Ubuntu.

- https://software.intel.com/en-us/node/705675#ubuntu

Other information

- https://software.intel.com/en-us/node/700692


Install the Ubuntu for the remote PC (Desktop or Laptop PC)
-----------------------------------------------------------

Download the ``Ubuntu 16.04.1`` version for desktop PC from the address below.

- https://www.ubuntu.com/download/desktop

If you need some help installing Ubuntu, please check out step-by-step guide below.

- https://www.ubuntu.com/download/desktop/install-ubuntu-desktop

Install the ROS and packages (SBCs and Remote PC)
-------------------------------------------------

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

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-urg-c ros-kinetic-urg-node ros-kinetic-rplidar-ros ros-kinetic-astra-camera ros-kinetic-astra-launch ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base

.. code-block:: bash

  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
  cd ~/catkin_ws && catkin_make

If catkin_make completes successfully without any errors, you have completed the preparation to use TurtlebBot3.


Network Configuration
---------------------

.. image:: _static/software/network_configuration.png


OpenCR
------

Let's build the OpenCR Arduino development environment.

1. USB settings
~~~~~~~~~~~~~~~

Allows the OpenCR USB port to be used in the ``Arduino IDE`` without root privileges.

.. code-block:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

2. Install the Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~~~~~

Download the latest version of ``Arduino IDE`` from the official arduino site and install it. At present, OpenCR is confirmed to be running in version ``1.16.0`` or later.

https://www.arduino.cc/en/Main/Software

When installing, unzip the downloaded compressed file into the desired folder and execute the installation file from the terminal as follows. For reference, the example below uses the folder named ``tools`` in the user's top folder (``~/``) as the Arduino IDE folder.

.. code-block:: bash

  cd ~/tools/arduino-1.6.12
  ./install.sh

Finally, add the location of the ``Arduino IDE`` installed above to the absolute path setting named ``PATH`` in the ``bashrc`` file as shown below. Add the following path to bashrc with the gedit editor (you can use another editor that you are comfortable with) and use the ``source`` command to apply the changes.

.. code-block:: bash

  gedit ~/.bashrc
  export PATH=$PATH:$HOME/tools/arduino-1.6.12
  source ~/.bashrc

3. Run the Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~

When running the ``Arduino IDE`` on Linux, run the arduino command as shown below.

.. code-block:: bash

  arduino

.. image:: _static/preparation/ide0.png

4. Adding OpenCR board into Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Preferences

Run the ``Arduino IDE`` installed above (type arduino in the terminal window) and click ``File`` → ``Preferences`` in the top menu of the IDE. When the Preferences screen appears, copy and paste the following link into the ``Additional Boards Manager URLs`` field.

.. code-block::

  https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json

.. image:: _static/preparation/ide1.png

2) Install the OpenCR package via Boards Manager

``Tools`` → ``Board`` → ``Boards Manager``.

.. image:: _static/preparation/ide2.png

Click ``OpenCR by ROBOTIS`` at the bottom to activate the ``Install`` button. Click this to install the OpenCR package.

.. image:: _static/preparation/ide3.png

When the installation is complete, you will see the following message: "INSTALLED".

.. image:: _static/preparation/ide4.png

If you look at the list of ``Tools`` → ``Board`` again, you can see that ``OpenCR Board`` is added at the bottom. Click this to add the OpenCR Board.

.. image:: _static/preparation/ide5.png

3) Port setting


This is the port setting for writing programs to Arduino IDE in OpenCR. To do this, OpenCR must be connected to a PC and OpenCR via USB.
 
Select ``Tools`` → ``Port`` → ``/dev/ttyACM0``.

.. WARNING:: The value of ``/dev/ttyACM0`` may be different depending on the environment connected to the PC.

.. image:: _static/preparation/ide6.png

5. Remove modemmanager
~~~~~~~~~~~~~~~~~~~~~~

After programming in the Arduino IDE and downloading the program to OpenCR, OpenCR will be restarted, at which time OpenCR and USB will be reconnected. At this time, the modem related package of Linux sends AT command to manage it. This indicates an OpenCR connection error, so you should remove the relevant package. Let's remove modemmanager as follows.

.. code-block:: bash

  sudo apt-get purge modemmanager


6. Bootloader writing
~~~~~~~~~~~~~~~~~~~~~~

The STM32F7xx, which is used as the main MCU on the OpenCR board, supports DFU(Device Firmware Upgrade). This enables the built-in bootloader of the MCU itself to boot the DFU protocol using USB, primarily for the bootloader initialization, recovery mode, and bootloader update. The biggest advantage is that you can user bootloader with USB without any other JTAG equipment. Let's write firmware using the DFU mode embedded in MCU without writing / debugging equipment such as STLink.

1) Programmer Setting

Select ``Tools`` → ``DFU-UTIL``

.. image:: _static/preparation/ide7.png

2) Run DFU mode

Pressing the ``Reset`` button while holding down the ``Boot`` button activates the DFU mode.

.. image:: _static/preparation/ide8.png

3) Download the bootloder

Click ``Tools`` → ``Burn Bootloader`` to download the bootloader.

.. image:: _static/preparation/ide9.png

7. Add the TurtleBot3 firmware into OpenCR
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(TODO)

.. _ROS: http://wiki.ros.org
