Bringup
=======

SBC
---

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_lds.launch
  stty -F /dev/ttyACM0

Remote PC
---------

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_pc.launch
