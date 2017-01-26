Bringup
=======

SBC
---

TurtleBot3 Basic
~~~~~~~~~~~~~~~~

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_lds.launch
  stty -F /dev/ttyACM0

TurtleBot3 Premium
~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  sudo chmod a+rw /dev/ttyUSB0
  roslaunch turtlebot3_bringup turtlebot3_bringup_sbc_r200.launch
  stty -F /dev/ttyACM0

Remote PC
---------

TurtleBot3 Basic
~~~~~~~~~~~~~~~~

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_pc_basic.launch

TurtleBot3 Premium
~~~~~~~~~~~~~~~~~~

.. code-block:: bash

  roslaunch turtlebot3_bringup turtlebot3_bringup_pc_premium.launch
