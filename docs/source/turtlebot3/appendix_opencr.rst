Appendix #OpenCR
================

.. image:: images/appendix/opencr/opencr.png

Overview
--------

``OpenCR`` is a main controller board of the TurtleBot3. The OpenCR, or the Open-source Control module for ROS, is developed for the ROS embedded system, providing with full open-source hardware and software. Everything of the board, including Schematics, PCB Gerber, BOM, and the firmware source for the TurtleBot3 can be freely distributed under open-source licenses for the users and the ROS community.

The STM32F7 series, which is a main chip inside the OpenCR board, has a very powerful ARM Cortex-M7 with floating point unit. The develop environment for the OpenCR is supported in the range from the Arduino IDE and Scratch for young students to the traditional firmware develop environment for the experts.

The board provides a set of digital and analog input/output pins that can interface from pne circuit to another or the built-in IMU sensor. The board is featured by the communication interfaces, including USB, which communicates with the PC, and UART, SPI, I2C, CAN for other embedded device.

To use a SBC, OpenCR board can give a best solution. It supports some power outputs: 12V, 5V, 3.3V for the SBCs and the sensors. It has also a hotswap feature in two external power inputs: the Battery and the SMPS.

Use this board to fill the imagined embedded control.


.. raw:: html

  <iframe width="640" height="360" src="https://www.youtube.com/embed/-_kBfIS6wJs" frameborder="0" allowfullscreen></iframe>

|


Specification
-------------

+--------------------------+--------------------------------------------------------------------+
| Items                    | Specifications                                                     |
+==========================+====================================================================+
| Microcontroller          | STM32F746NGH6 / 32-bit ARM Cortex®-M7 with  FPU (216MHz, 462DMIPS) |
+--------------------------+--------------------------------------------------------------------+
| Sensors                  | Gyroscope 3Axis, Accelerometer 3Axis, Magnetometer 3Axis (MPU9250) |
+--------------------------+--------------------------------------------------------------------+
| Programmer               | ARM Cortex 10pin JTAG/SWD connector                                |
+                          +--------------------------------------------------------------------+
|                          | USB Device Firmware Upgrade (DFU)                                  |
+                          +--------------------------------------------------------------------+
|                          | Serial                                                             |
+--------------------------+--------------------------------------------------------------------+
| Extension pins           | 32 pins (L 14, R 18) *Arduino connectivity                         |
+                          +--------------------------------------------------------------------+
|                          | Sensor module x 4 pins                                             |
+                          +--------------------------------------------------------------------+
|                          | Extension connector x 18 pins                                      |
+--------------------------+--------------------------------------------------------------------+
| Communication circuits   | USB (Micro-B USB connector/USB 2.0/Host/Peripehral/OTG)            |
+                          +--------------------------------------------------------------------+
|                          | TTL (JST 3pin / Dynamixel)                                         |
+                          +--------------------------------------------------------------------+
|                          | RS485 (JST 4pin / Dynamixel)                                       |
+                          +--------------------------------------------------------------------+
|                          | UART x 2                                                           |
+                          +--------------------------------------------------------------------+
|                          | CAN                                                                |
+--------------------------+--------------------------------------------------------------------+
| LEDs and buttons         | LD2 (red/green) : USB communication                                |
+                          +--------------------------------------------------------------------+
|                          | User LED x 4 : LD3 (red), LD4 (green), LD5 (blue)                  |
+                          +--------------------------------------------------------------------+
|                          | User button  x 2                                                   |
+--------------------------+--------------------------------------------------------------------+
| Powers                   | External input source                                              |
+                          +--------------------------------------------------------------------+
|                          | 5 V (USB VBUS), 7-24 V (Battery or SMPS)                           |
+                          +--------------------------------------------------------------------+
|                          | Default battery : LI-PO 11.1V 1,800mAh 19.98Wh                     |
+                          +--------------------------------------------------------------------+
|                          | Default SMPS: 12V 5A                                               |
+                          +--------------------------------------------------------------------+
|                          | External output source                                             |
+                          +--------------------------------------------------------------------+
|                          | 12V@1A, 5V@4A, 3.3V@800mA                                          |
+                          +--------------------------------------------------------------------+
|                          | External battery connect for RTC (Real Time Clock)                 |
+                          +--------------------------------------------------------------------+
|                          | Power LED: LD1 (red, 3.3 V power on)                               |
+                          +--------------------------------------------------------------------+
|                          | Reset button x 1 (for power reset of board)                        |
+                          +--------------------------------------------------------------------+
|                          | Power on/off switch x 1                                            |
+--------------------------+--------------------------------------------------------------------+
| Dimensions               | 105(W) X 75(D) mm                                                  |
+--------------------------+--------------------------------------------------------------------+
| Mass                     | 60g                                                                |
+--------------------------+--------------------------------------------------------------------+

* Hot-swap for switching from "shore power"(12V, 5A SMPS) to "mobile power"(battery): power board to support uninterruptible power supply (UPS) type of functionality.

User's guide
------------

Run serial_node package
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  rosrun rosserial_python serial_node.py __name:=turtlebot3_core _port:=/dev/ttyACM0 _baud:=115200

Testing
~~~~~~~

.. code-block:: bash

  rostopic echo /imu

  header:
    seq: 179
    stamp:
      secs: 1486448047
      nsecs: 147523921
    frame_id: imu_link
  orientation:
    x: 0.0165222994983
    y: -0.0212152898312
    z: 0.276503056288
    w: 0.960632443428
  orientation_covariance: [0.0024999999441206455, 0.0, 0.0, 0.0, 0.0024999999441206455, 0.0, 0.0, 0.0, 0.0024999999441206455]
  angular_velocity:
    x: 2.0
    y: 1.0
    z: -1.0
  angular_velocity_covariance: [0.019999999552965164, 0.0, 0.0, 0.0, 0.019999999552965164, 0.0, 0.0, 0.0, 0.019999999552965164]
  linear_acceleration:
    x: 528.0
    y: 295.0
    z: 16648.0
  linear_acceleration_covariance: [0.03999999910593033, 0.0, 0.0, 0.0, 0.03999999910593033, 0.0, 0.0, 0.0, 0.03999999910593033]
  ---

GitHub repository
-----------------

https://github.com/ROBOTIS-GIT/OpenCR

Detail wiki site
----------------

https://github.com/ROBOTIS-GIT/OpenCR/wiki
