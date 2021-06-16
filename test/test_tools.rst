Title: Tools to perform test on a ROS system
Author: Nadia Hammoudeh Garcia <nadia.hammoudeh.garcia@ipa.fraunhofer.de>
Status: Active
Type: Tool
Content-Type: text/x-rst
Created: 15-April-2021

Abstract
========

This document summarizes the best practices and available tools to test and debug ROS code and systems


Software quality
================

wiki + developers' discussions
------------------------------
http://wiki.ros.org/Quality
http://wiki.ros.org/Quality/Tutorials
https://discourse.ros.org/c/quality/37

Package Quality categories
---------------------------
REP 2004:  
https://ros.org/reps/rep-2004.html
https://github.com/ros-infrastructure/rep/pull/218
https://github.com/ros2/ros2_documentation/pull/460

Discussion about maintaining a central list of packages by quality level: https://discourse.ros.org/t/list-of-ros2-packages-by-quality-level-re-rep2004-3-v-b/19978

Developers' guide to write good quality ROS code:
https://docs.ros.org/en/foxy/Contributing/Developer-Guide.html
https://docs.ros.org/en/foxy/Contributing/Quality-Guide.html

Testing
=======

Levels of testing
-----------------
Level 1. Library unit test (unittest, gtest)  

Level 2. ROS node unit test (rostest + unittest/gtest): Node unit tests start up your node and test its external API, i.e. published topics, subscribed topics, and services.
http://wiki.ros.org/rostest/Nodes
https://github.com/ros/ros_comm/blob/29053c4832229efa7160fb944c05e3bc82e11540/tools/rostest/nodes/publishtest
http://wiki.ros.org/rostest/Nodes#publishtest

Level 3. ROS nodes integration/regression test (rostest + unittest/gtest): Integration tests start up multiple nodes and test that they all work together as expected.
https://github.com/ros/ros_comm/blob/29053c4832229efa7160fb944c05e3bc82e11540/tools/rostest/test/publishtest.test
https://industrial-training-master.readthedocs.io/en/melodic/_source/session6/Unit-Testing.html


Testing frameworks
------------------
C++:  
gtest: http://wiki.ros.org/gtest
catch: https://github.com/AIS-Bonn/catch_ros

python:  
http://wiki.ros.org/unittest

Fuzzing:  
https://github.com/rosin-project/ros2_fuzz
https://github.com/rosin-project/rclcpp_fuzz

Use-cases:  
Though meant for PX4, still a useful guide: https://dev.px4.io/v1.11_noredirect/en/test_and_ci/
Developers' discussion about robot testing practices: https://discourse.ros.org/t/best-practices-for-robot-testing/16608

ROS2 testing
------------
https://github.com/ros2/system_tests
integration testing: https://index.ros.org/p/launch_testing/
launch_testing example: https://github.com/ros2/system_tests/blob/89e31050b78b4bdd792f6e3da444d01cd7d8a147/test_rclcpp/test/test_executable_output.py.in
https://vimeo.com/378683186

Performance Testing
-------------------
Paper by Apex.AI: https://drive.google.com/file/d/15nX80RK6aS8abZvQAOnMNUEgh7px9V5S/view

---
Testing lossy networks (especially for QoS settings in ROS2): https://docs.ros.org/en/foxy/Tutorials/Quality-of-Service.html

Continuous Integration 
----------------------
http://wiki.ros.org/Quality/Tutorials/Continuous%20integration%20with%20the%20public%20infrastructure

Github actions:  
https://github.com/ros-tooling/action-ros-ci
https://github.com/ros-tooling/setup-ros
For mixed systems (ROS1 and ROS2): https://github.com/ros2/ros1_bridge/blob/master/.github/workflows/main.yml
CI on real robots by Fetch Robotics at ROSCon: https://vimeo.com/187705231

Debugging
=========
GDB (http://sourceware.org/gdb/)
Oprofile (http://oprofile.sourceforge.net/news/)
Valgrind (http://valgrind.org/)

Using GDB to run a ROS node
```
rosrun --prefix "gdb --args" package node
```
Using GDB / Valgrind in launch files:  
http://wiki.ros.org/roslaunch/Tutorials/Roslaunch%20Nodes%20in%20Valgrind%20or%20GDB


Section AAAA
=============

Sub-section AAAAA
----------------

....

Sub-section AAAAAA
----------------

....

Section BBBB
=============

Sub-section BBBBB
----------------

....

Sub-section BBBBBB
----------------

....

Motivation
==========

...

Rationale
=========

.....


Compatibility
=======================

Was developed for a concrete DISTRO? 
Is it compatble with ROS and ROS2?


Software updates to support other distros or systems
----------------------------------------------------

(optional section, only if relevant)


Bugs and limitations
====================

Known bugs or limitations. 

ideas about potential improvements?

Reference implementation
========================


Link to code and instructions to install and run the feature or tool


References
==========

.. [#fhs] ROS
   (https://www.ros.org)

.. [#fhs] Relavant discourse discussion
   (https://discourse.ros.org/....)
   
Copyright
=========

This document has been placed in the public domain.

..
   Local Variables:
   mode: indented-text
   indent-tabs-mode: nil
   sentence-end-double-space: t
   fill-column: 70
   coding: utf-8
   End:

