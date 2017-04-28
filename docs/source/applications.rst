Applications
============

This section shows some demos using Turtlebot3.
For implementing you have to install the turtlebot3_applications package.

.. NOTE:: The Turtlebot3 has been tested on ``Ubuntu 16.04`` and ``ROS Kinetic Kame`` version.

.. TIP:: Terminal is opened to go to the Ubuntu search icon, type "Terminal" or use Ctrl-Alt-T.

[``Remote PC``] Go to  ROS source directory (/home/<user_name>/catkin_ws/src) and clone the turtlebot3_applications repository.

.. code-block:: bash

  cd ~/catkin_ws/src
  git clone https://github.com/ROBOTIS-GIT/turtlebot3_applications.git

[``Remote PC``] catkin_make to install the new package

.. code-block:: bash

 cd ~/catkin_ws && catkin_make


TurtleBot Follower Demo
-----------------------

.. NOTE:: Turtlebot Follower Demo requires scikit-learn, NumPy and ScyPy packages. Instructions for installing are found in http://scikit-learn.org/stable/install.html

The robot follower demo was implemented using only HLS-LFCD LDS, a classification algorithm is used based on previous fitting with samples of person and obstacles positions to take actions. It follows someone in front of the robot inside the 1 meter range and 120 degrees.

[``Remote PC``] Move to turtlebot3_follower source directory

.. code-block:: bash

  roscd turtlebot3_follower/src/

[``Remote PC``] Run Turtlebot3 Follower demo

.. code-block:: bash

  rosrun turtlebot3_follower follower.py


TurtleBot Panorama Demo Using Raspberry Pi Camera Module
--------------------------------------------------------

.. NOTE:: The turtlebot3_panorama demo uses pano_ros for taking snapshots and stitching them together to create panorama pictures.
.. NOTE:: Panorama Demo requires to have Raspicam package installed. Instructions for installing this package can be found in https://github.com/UbiquityRobotics/raspicam_node
.. NOTE:: Panorama Demo requires to have OpenCV and cvbridge package. Instructions for installing OpenCV are found in http://docs.opencv.org/2.4/doc/tutorials/introduction/linux_install/linux_install.html

[``TurtleBot``] Launch the Raspberry Pi cam V2

.. code-block:: bash

  roslaunch raspicam_node camerav2_1280x960.launch

[``Remote PC``] Launch Panorama

.. code-block:: bash

  roslaunch turtlebot3_panorama panorama.launch

[``Remote PC``] To start the panorama demo

.. code-block:: bash

  rosservice call turtlebot3_panorama/take_pano 0 360.0 30.0 0.3


Parameters that can be sent to the rosservice to take a pano are:

- mode for taking the pictures. Can be:
    0 for snap&rotate (i.e. rotate, stop, snapshot, rotate, stop, snapshot, ...)
    1 for continuous (i.e. keep rotating while taking snapshots)
    2 to stop an ongoing panorama creation
- total angle of panorama picture, in degrees
- angle interval (in degrees) when creating the panorama picture in snap&rotate mode, time interval (in seconds) otherwise
- rotating velocity (in radians/s)


[``Remote PC``] To view the results

.. code-block:: bash

  rqt_image_view image:=/turtlebot3_panorama/panorama


.. image:: _static/application/panorama_view.png

Automatic Docking
-----------------

(TODO)
