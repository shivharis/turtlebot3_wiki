Appendix #OpenCR
================

.. image:: _static/appendix/opencr/opencr.jpg

Overview
--------

We are using ``OpenCR`` as the main controller for TurtleBot3. OpenCR means Open-source Control module for ROS. It targets the ROS embedded system, with full open-source hardware and software. It uses the STM32F7 series as main chip. It has very powerful ARM Cortex-M7 with floating point unit. It supports Arduino IDE and Scratch for young students and traditional firmware develop environment. So you can choose the way to programming up to your develop environment. Also, we will provide everything of this board including Schematics, PCB Gerber, BOM, firmware for turtlebot3 with open-source licenses for you and ROS community.

This board provide sets of digital and analog input/output pins that can interface to other circuits and built-in IMU sensor. The board has a feature in communication interfaces, including USB, for loading programs from personal computers and UART, SPI, I2C, CAN for other embedded device.

If you want to use a SBC, OpenCR board is best solution for you. It support Powerful external output source: 12V, 5V, 3.3V for SBCs and sensors. Also, it has hotswap feature on two external input source Battery and SMPS. Many ideas are giving from Morgan, Thanks Morgan!

If the embedded control is required along with a SBC to make a robot, we strongly recommend this board.

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
| Extension pins           | 32 pins (L 14, R 18) *Arduino Uno Revision 3 connectivity          |
+                          +--------------------------------------------------------------------+
|                          | Sensor x 4 pins                                                    |
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
|                          | : 5 V (USB VBUS), 7-24 V (Battery or SMPS)                         |
+                          +--------------------------------------------------------------------+
|                          | : Default battery: LI-PO 11.1V 1,800mAh 19.98Wh                    |
+                          +--------------------------------------------------------------------+
|                          | : Defalut SMPS: 12V 5A                                             |
+                          +--------------------------------------------------------------------+
|                          | External output source                                             |
+                          +--------------------------------------------------------------------+
|                          | : 12V@1A, 5V@4A, 3.3V@800mA                                        |
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

GitHub repository
-----------------

https://github.com/ROBOTIS-GIT/OpenCR

Detail wiki site
----------------

(TODO)
