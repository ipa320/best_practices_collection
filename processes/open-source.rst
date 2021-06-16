| Title: Open-sourcing code
| Author: Nadia Hammoudeh Garcia <nhg@ipa.fraunhofer.de>
| Status: Active
| Type: trong recommendation 
| Content-Type: text/x-rst
| Created: 15-June-2021

Abstract
========

This document holds some generic recommendations about how to open source software to the ROS community.

Steps to open source existing software
======================================

Steps to open-source the software:

1) Split the packages into stacks/repositories
----------------------------------------------

Generally speaking, these are the criteria for the organisation of repositories:
  - packages with robot-agnostic software
  - packages with robot specific configuration (description and launch files for real robot and gazebo)
  - project specific packages (?) is this really needed or can be merged with the robot specific configurations?

The second division criteria are the dependencies, 2 things have to be considered here:
  - future release of the software: in case you plan to release  your packages (rosdistro official release) you will need that all the dependencies of the project are previously released. Then you should create stacks of packages that depends on stable package or blocks of packages (for example that depends on the Moveit! stack).
  - "weight" of the packages and their dependencies. Very commonly we separate source code and gazebo related packages. The gazebo and rviz packages are quite heavy and there is no need to install them on a computer that will be used to work only with the real robot.

2) Add a license type. 
----------------------
The type of the license has to be added to the package.xml of all the package within the repository. Apart of this the repository has to hold a file called LICENSE with the clause of the selected license. GitHub provide template for the most common licenses types, see https://docs.github.com/es/communities/setting-up-your-project-for-healthy-contributions/adding-a-license-to-a-repository for further information.

For ROS we usually recommend Apache 2.0 it is the less restrictive. The BSD is also ok for ROS packages.

3) Review all the package.xml and complete the list of dependencies
-------------------------------------------------------------------

The correct definition of dependencies in ROS is essential, it significantly reduces the time to transfer the software to another device or deployme tasks. Please check the following official documentation: https://docs.ros.org/en/melodic/api/catkin/html/howto/format2/index.html

4) Add CI configuration
-----------------------
We strongly recommend the use of the stack industrial_ci: https://github.com/ros-industrial/industrial_ci. The Test tools document contains a more extensive list of existing tools: https://github.com/ipa320/best_practices_collection/blob/main/test/test_tools.rst#continuous-integration 

5) Add a good documentation
---------------------------

This step is optional but highly recommended to win visibility.

Motivation
==========

Standarizacion and simplification of the process to open source existing software.


Compatibility
=======================

This documentation is valid for all the ROS versions

   
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

