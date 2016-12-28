Preparation
===========

Configuring your Raspberry Pi 3
-------------------------------

1. Install the Ubuntu MATE for the Raspberry Pi 3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

https://ubuntu-mate.org/raspberry-pi/

2. Install the ROS
~~~~~~~~~~~~~~~~~~

.. code:: bash

  wget https://raw.githubusercontent.com/oroca/oroca-ros-pkg/kinetic/ros_install.sh && chmod 755 ./ros_install.sh && bash ./ros_install.sh catkin_ws kinetic

.. code:: bash

  git clone https://github.com/ROBOTIS-GIT/turtlebot3.git

.. code:: bash

  sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-urg-c ros-kinetic-urg-node ros-kinetic-rplidar-ros ros-kinetic-astra-camera ros-kinetic-astra-launch ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base

.. code:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

Configuring your OpenCR
-----------------------

Let's build the OpenCR Arduino development environment.

1. USB settings
~~~~~~~~~~~~~~~

Allows the OpenCR USB port to be used in the Arduino IDE without root privileges.

.. code:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

2. Install the Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~~~~~

Download the latest version of Arduino IDE from the official arduino site and install it. At present, OpenCR is confirmed to be running in version 1.16.0 or later.

https://www.arduino.cc/en/Main/Software

When installing, unzip the downloaded compressed file into the desired folder and execute the installation file from the terminal as follows. For reference, the example below uses the folder named 'tools' in the user's top folder (~/) as the Arduino IDE folder.

.. code:: bash

  cd ~/tools/arduino-1.6.12
  ./install.sh

Finally, add the location of the Arduino IDE installed above to the absolute path setting named PATH in the bashrc file as shown below. Add the following path to bashrc with the gedit editor (you can use another editor that you are comfortable with) and use the 'source' command to apply the changes.

.. code:: bash

  gedit ~/.bashrc
  export PATH=$PATH:$HOME/tools/arduino-1.6.12
  source ~/.bashrc

3. Run the Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~

When running the Arduino IDE on Linux, run the arduino command as shown below.

.. code:: bash

  arduino

.. image:: _static/preparation/ide0.png

4. Adding OpenCR board into Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1) Preferences

Run the Arduino IDE installed above (type arduino in the terminal window) and click [File] -> [Preferences] in the top menu of the IDE. When the Preferences screen appears, copy and paste the following link into the [Additional Boards Manager URLs] field.

.. code::

  https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json

.. image:: _static/preparation/ide1.png

2) Install the OpenCR package via Boards Manager

[Tools] -> [Board] -> [Boards Manager].

.. image:: _static/preparation/ide2.png

Click [OpenCR by ROBOTIS] at the bottom to activate the [Install] button. Click this to install the OpenCR package.

.. image:: _static/preparation/ide3.png

When the installation is complete, you will see the following message: "INSTALLED".

.. image:: _static/preparation/ide4.png

If you look at the list of [Tools] -> [Board] again, you can see that [OpenCR Board] is added at the bottom. Click this to add the OpenCR Board.

.. image:: _static/preparation/ide5.png

3) Port setting


This is the port setting for writing programs to Arduino IDE in OpenCR. To do this, OpenCR must be connected to a PC and OpenCR via USB.
 
Select [Tools] -> [Port] -> [/ dev / ttyACM0].

.. WARNING:: The value of '/dev/ttyACM0' may be different depending on the environment connected to the PC.

.. image:: _static/preparation/ide6.png

6. Remove modemmanager
~~~~~~~~~~~~~~~~~~~~~~

After programming in the Arduino IDE and downloading the program to OpenCR, OpenCR will be restarted, at which time OpenCR and USB will be reconnected. At this time, the modem related package of Linux sends AT command to manage it. This indicates an OpenCR connection error, so you should remove the relevant package. Let's remove modemmanager as follows.

.. code:: bash

  sudo apt-get purge modemmanager


7. bootloader writing
~~~~~~~~~~~~~~~~~~~~~~

The STM32F7xx, which is used as the main MCU on the OpenCR board, supports DFU(Device Firmware Upgrade). This enables the built-in bootloader of the MCU itself to boot the DFU protocol using USB, primarily for the bootloader initialization, recovery mode, and bootloader update. The biggest advantage is that you can user bootloader with USB without any other JTAG equipment. Let's write firmware using the DFU mode embedded in MCU without writing / debugging equipment such as STLink.

1) Programmer Setting

Select [Tools] -> [DFU-UTIL]

.. image:: _static/preparation/ide7.png

2) Run DFU mode

Pressing the [Reset] button while holding down the [Boot] button activates the DFU mode.

.. image:: _static/preparation/ide8.png

3) Download the bootloder

Click [Tools] -> [Burn Bootloader] to download the bootloader.

.. image:: _static/preparation/ide9.png

5. Add the TurtleBot3 firmware into OpenCR
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(TODO)

Components
----------

Turtlebot is divided into Basic model and Premium model according to the components as shown in the table below. The biggest difference is the type of motor used and the configuration of SBC and Sensor.

+------------+--------------------------+--------+---------+
|            |                          | Basic  | Premium |
+============+==========================+========+=========+
|            | item                     | number | number  |
+------------+--------------------------+--------+---------+
|            | Waffle-plate             | 8      | 24      |
+            +--------------------------+--------+---------+
|            | Plate-support            | 10     | 20      |
+            +--------------------------+--------+---------+
|            | Board-support            | 10     | 10      |
+            +--------------------------+--------+---------+
|            | Wheel                    | 2      | 2       |
+            +--------------------------+--------+---------+
| Frame      | Rubber tire              | 2      | 2       |
+            +--------------------------+--------+---------+
| Wheel      | Ball caster              | 1      | 2       |
+            +--------------------------+--------+---------+
|            | Bolt and nut set         | 1      | 1       |
+            +--------------------------+--------+---------+
|            | Dream plate 5x5 K        | 1      | 1       |
+            +--------------------------+--------+---------+
|            | Dream L-bracket 2P K     | 1      | 1       |
+            +--------------------------+--------+---------+
|            | Rivet set                | 10     | 10      |
+------------+--------------------------+--------+---------+
|            | XL430-W350-T             | 2      | x       |
+            +--------------------------+--------+---------+
|            | Horn for XL430           | 2      | x       |
+ Motor      +--------------------------+--------+---------+
|            | XM430-W350-T             | x      | 2       |
+            +--------------------------+--------+---------+
|            | Horn for XM430           | x      | 2       |
+------------+--------------------------+--------+---------+
| Controller | OpenCR                   | 1      | 1       |
+------------+--------------------------+--------+---------+
|            | SMPS 12V 5A              | 1      | 1       |
+            +--------------------------+--------+---------+
|            | LIPO 11.1V 1800mAh       | 1      | 1       |
+            +--------------------------+--------+---------+
| Power      | Battery conversion cable | 1      | 1       |
+            +--------------------------+--------+---------+
| Battery    | Velcro                   | 2      | 2       |
+            +--------------------------+--------+---------+
| Cable      | Robot Cable-X3P 180mm    | 2      | 2       |
+            +--------------------------+--------+---------+
|            | Robot Cable-X3P 240mm    | x      | 2       |
+            +--------------------------+--------+---------+
|            | LIPO Battery Charger     | 1      | 1       |
+            +--------------------------+--------+---------+
|            | MicroUSB cable           | 1      | 1       |
+            +--------------------------+--------+---------+
|            | SBC power cable          | 1      | 1       |
+------------+--------------------------+--------+---------+
|            | RaspberryPi 3 model B    | 1      | x       |
+ SBC        +--------------------------+--------+---------+
|            | Intel Joule              | x      | 1       |
+------------+--------------------------+--------+---------+
|            | Laser Distance Sensor    | 1      | 1       |
+ Sensor     +--------------------------+--------+---------+
|            | Intel Realsense R200/400 | x      | 1       |
+------------+--------------------------+--------+---------+

Assembly
--------

Turtlebots are delivered in a single package, not each assembly. In order for the user to use TurtleBot, it is necessary to assemble according to the following procedure.

Basic model
~~~~~~~~~~~

(TODO)

Premium model
~~~~~~~~~~~~~

(TODO)
