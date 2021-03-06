^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package opencv_apps
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1.11.14 (2016-09-12)
--------------------

* Force convert to bgr for display (`#30 <https://github.com/ros-perception/opencv_apps/issues/30>`_)

  * add include sensor_msgs/image_encodings for old image_encodings
  * force conver to bgr8 using sensor_msgs::image_encodings::BGR8

* Add more nodes from opencv sample codes

  * [smoothing] Add smoothing filter sample code, test, launch files (`#32 <https://github.com/ros-perception/opencv_apps/issues/32>`_)
  * [threshold] add threshold sample code (`#27 <https://github.com/ros-perception/opencv_apps/issues/27>`_)
  * [adding_image] add adding_image sample code (`#29 <https://github.com/ros-perception/opencv_apps/issues/29>`_)

* Add launch files for opencv_apps nodes

  * separate launch and test files (`#20 <https://github.com/ros-perception/opencv_apps/issues/20>`_)

* Add hydro travis testing (`#22 <https://github.com/ros-perception/opencv_apps/issues/22>`_)

  * test/CMakeLists.txt : catkin_download_test_data not working with DESTINATION . for hydro
  * cv_bridge before 1.11.9 does not suport CompressedImage in cv_bridge
  * lk_flow : need to explicitly include sensor_msgs/image_endcodings.h
  * simple_compressed_example_nodelet.cpp : need to include sensor_msgs/CompressedImage explicitly on hydro
  * .travis.yml : add hydro testing

* Minor Fixes

  * update gitignore to avoid test png data (`#28 <https://github.com/ros-perception/opencv_apps/issues/28>`_)
  * fix  hough_circles for input frame color (`#13 <https://github.com/ros-perception/opencv_apps/issues/13>`_ )
  * CMakeLists.txt update list of opencv tutorial codes (`#25 <https://github.com/ros-perception/opencv_apps/issues/25>`_)
  * fix face_detection.launch to accept args for cascade xml for opencv3 (`#20 <https://github.com/ros-perception/opencv_apps/issues/20>`_)
  * CMakeLists.txt : add install rule for launch (`#20 <https://github.com/ros-perception/opencv_apps/issues/20>`_)
  * add launch/*.launch files (from test/*.test) to reuse launch files (`#20 <https://github.com/ros-perception/opencv_apps/issues/20>`_)
  * CMakeLists.txt: on roslaunch 1.11.1, roslaunch_add_file check fails with unsupported doc attributes (`#20 <https://github.com/ros-perception/opencv_apps/issues/20>`_)
  * 

* Add test for simple_example / simple_compressed_example (`#24 <https://github.com/ros-perception/opencv_apps/issues/24>`_)

  * add retry for simple_example/simple_compressed_example test, not sure why it fails.. on travis
  * package.xml : add image_transport_plugins to test_depend for republish node in test-simple_compressed_example.test
  * add test for simple_example/simple_compressed_example
  * simple_example_nodlet.cpp / simple_compressed_example_nodelet.cpp : support debug_view param
  * .travis.sh : add catkin_test_results --verbose

* Support kinetic on travis (`#15 <https://github.com/ros-perception/opencv_apps/issues/15>`_)

  * test/test-face-detection.test : add haarcascade data from opencv3 package directory
  * use docekr to run trusty/xenial .travis.sh

* Modified enabling use_camera_info by rosparam (`#18 <https://github.com/ros-perception/opencv_apps/issues/18>`_)
  
  * Enabling dynamic_reconfigure in private nodelet handler

* Enable to set min_distance_between_circles param, publish debug message (`#14 <https://github.com/ros-perception/opencv_apps/issues/14>`_)

  * hough_circles : fix to set dp_int to dp
  * hough_circles : enable to set min_distance_between_circles
  * hough_circles : add debug_image_publisher
  * hough_circles : fix bugs on createTrackver uses gaussian_blur_size for sigma x/y

* Contributors: Kei Okada, Iori Yanokura

1.11.13 (2016-06-01)
--------------------
* Add parameter to people_detector `#9 <https://github.com/ros-perception/opencv_apps/issues/9>`_
* hough_circles: enable to set double value to the HoughCircle params `#8 <https://github.com/ros-perception/opencv_apps/issues/8>`_

  * hough_circle enable to set gaussian_blue_size and kernel sigma from cfg
  * hough_circles: fix default/min/max value of cfg
  * hough_circle: enable to set db to 100
  * circle_hough: dp, accumrate_threshold, canny_threshold is double, not int

* Add parameter to hough_circles_nodelet `#7 <https://github.com/ros-perception/opencv_apps/issues/7>`_
* Add parameter to hough_lines_nodelet `#6 <https://github.com/ros-perception/opencv_apps/issues/6>`_
* Add parameter to edge_detection_nodelet(canny) `#5 <https://github.com/ros-perception/opencv_apps/issues/5>`_
* Simplify source tree by removing duplicated node codes `#4 <https://github.com/ros-perception/opencv_apps/issues/4>`_  Closes `#3 <https://github.com/ros-perception/opencv_apps/issues/3>`_
* fix .travis file
* copy Travis and .gitignore from vision_opencv
* geometry_msgs doesn't get used by opencv_apps, but std_msgs does. (`#119 <https://github.com/ros-perception/vision_opencv/pull/119>`_)
* Contributors: Kei Okada, Kentaro Wada, Lucas Walter, Vincent Rabaud, IorI Yanokura

1.11.12 (2016-03-10)
--------------------
* relax test condition
* fix test hz to 5 hz, tested on core i7 3.2G
* Refactor opencv_apps to remove duplicated codes to handle connection of
  topics.
  1. Add opencv_apps::Nodelet class to handle connection and disconnection of
  topics.
  2. Update nodelets of opencv_apps to inhereit opencv_apps::Nodelet class
  to remove duplicated codes.
* Contributors: Kei Okada, Ryohei Ueda

1.11.11 (2016-01-31)
--------------------
* check if opencv_contrib is available
* Use respawn instead of watch
* Contributors: Kei Okada, trainman419

1.11.10 (2016-01-16)
--------------------
* enable simple_flow on opencv3, https://github.com/ros-perception/vision_opencv/commit/8ed5ff5c48b4c3d270cd8216175cf6a8441cb046 can revert https://github.com/ros-perception/vision_opencv/commit/89a933aef7c11acdb75a17c46bfcb60389b25baa
* lk_flow_nodeletcpp, fback_flow_nodelet.cpp: need to copy input image to gray
* opencv_apps: add test programs, this will generate images for wiki
* fix OpenCV3 build
* phase_corr: fix display, bigger circle and line
* goodfeature_track_nodelet.cpp: publish good feature points as corners
* set image encoding to bgr8
* convex_hull: draw hull with width 4
* watershed_segmentatoin_nodelet.cpp: output segmented area as contours and suppot add_seed_points as input of segmentatoin seed
* src/nodelet/segment_objects_nodelet.cpp: change output image topic name from segmented to image
* Convert rgb image to bgr in lk_flow
* [oepncv_apps] fix bug for segment_objects_nodelet.cpp
* Contributors: Kei Okada, Kentaro Wada, Shingo Kitagawa, Vincent Rabaud

1.11.9 (2015-11-29)
-------------------
* Accept grayscale images as input as well
* Add format enum for easy use and choose format.
* Contributors: Felix Mauch, talregev

1.11.8 (2015-07-15)
-------------------
* simplify the OpenCV3 compatibility
* fix image output of fback_flow
* fix error: ISO C++ forbids initialization of member for gcc 4.6
* add std_srvs
* add std_srvs
* fix error: ISO C++ forbids initialization of member for gcc 4.6
* get opencv_apps to compile with OpenCV3
* fix licenses for Kei
* add opencv_apps, proposed in `#40 <https://github.com/ros-perception/vision_opencv/issues/40>`_
* Contributors: Kei Okada, Vincent Rabaud, Yuto Inagaki
