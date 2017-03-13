Applications
============

.. NOTE:: The Turtlebot3 has been tested on ``Ubuntu 16.04.1`` and ``ROS Kinetic Kame`` version.
.. NOTE:: The turtlebot3_panorama demo uses pano_ros for taking snapshots and stitching them together to create panorama pictures.


TurtleBot Follower Demo
-----------------------

(TODO)

TurtleBot Panorama Demo Using Raspberry Pi Camera Module
-----------------------

[TurtleBot3 SBC] Launch the raspberry pi cam V2

.. code-block:: bash

  roslaunch raspicam_node camerav2_1280x960.launch

 [Remote PC] Launch Panorama
 
.. code-block:: bash
  
 roslaunch turtlebot3_panorama panorama.launch 

 [Remote PC] To start the panorama demo
 
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


  [Remote PC] To view the results
  
.. code-block:: bash

  rqt_image_view image:=/turtlebot3_panorama/panorama


.. image:: images/application/panorama_view.png

Automatic Docking
-----------------

(TODO)
