OpenCR Software Setup
=====================

.. NOTE:: We tested the Turtlebot 3 on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.

OpenCR
------

Let's build the OpenCR Arduino development environment on remote PC.

USB settings
~~~~~~~~~~~~

Allows the OpenCR USB port to be used in the ``Arduino IDE`` without root privileges.

.. code-block:: bash

  wget https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/99-opencr-cdc.rules
  sudo cp ./99-opencr-cdc.rules /etc/udev/rules.d/
  sudo udevadm control --reload-rules

Install the Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~~

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

Run the Arduino IDE
~~~~~~~~~~~~~~~~~~~

When running the ``Arduino IDE`` on Linux, run the arduino command as shown below.

.. code-block:: bash

  arduino

.. image:: _static/preparation/ide0.png

Adding OpenCR board into Arduino IDE
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Preferences
...........

Run the ``Arduino IDE`` installed above (type arduino in the terminal window) and click ``File`` → ``Preferences`` in the top menu of the IDE. When the Preferences screen appears, copy and paste the following link into the ``Additional Boards Manager URLs`` field.

.. code-block::

  https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json

.. image:: _static/preparation/ide1.png

Install the OpenCR package via Boards Manager
.............................................

``Tools`` → ``Board`` → ``Boards Manager``.

.. image:: _static/preparation/ide2.png

Click ``OpenCR by ROBOTIS`` at the bottom to activate the ``Install`` button. Click this to install the OpenCR package.

.. image:: _static/preparation/ide3.png

When the installation is complete, you will see the following message: "INSTALLED".

.. image:: _static/preparation/ide4.png

If you look at the list of ``Tools`` → ``Board`` again, you can see that ``OpenCR Board`` is added at the bottom. Click this to add the OpenCR Board.

.. image:: _static/preparation/ide5.png

Port setting
............

This is the port setting for writing programs to Arduino IDE in OpenCR. To do this, OpenCR must be connected to a PC and OpenCR via USB.
 
Select ``Tools`` → ``Port`` → ``/dev/ttyACM0``.

.. WARNING:: The value of ``/dev/ttyACM0`` may be different depending on the environment connected to the PC.

.. image:: _static/preparation/ide6.png

Remove modemmanager
~~~~~~~~~~~~~~~~~~~

After programming in the Arduino IDE and downloading the program to OpenCR, OpenCR will be restarted, at which time OpenCR and USB will be reconnected. At this time, the modem related package of Linux sends AT command to manage it. This indicates an OpenCR connection error, so you should remove the relevant package. Let's remove modemmanager as follows.

.. code-block:: bash

  sudo apt-get purge modemmanager


Bootloader writing
~~~~~~~~~~~~~~~~~~

The STM32F7xx, which is used as the main MCU on the OpenCR board, supports DFU(Device Firmware Upgrade). This enables the built-in bootloader of the MCU itself to boot the DFU protocol using USB, primarily for the bootloader initialization, recovery mode, and bootloader update. The biggest advantage is that you can user bootloader with USB without any other JTAG equipment. Let's write firmware using the DFU mode embedded in MCU without writing / debugging equipment such as STLink.

Programmer Setting
..................

Select ``Tools`` → ``DFU-UTIL``

.. image:: _static/preparation/ide7.png

Run DFU mode
............

Pressing the ``Reset`` button while holding down the ``Boot`` button activates the DFU mode.

.. image:: _static/preparation/ide8.png

Download the bootloder
......................

Click ``Tools`` → ``Burn Bootloader`` to download the bootloader.

.. image:: _static/preparation/ide9.png

Add the TurtleBot3 firmware into OpenCR
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(TODO)

.. _ROS: http://wiki.ros.org
