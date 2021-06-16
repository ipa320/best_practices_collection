| Title: Tools to easily command the robot actuators
| Author: Nadia Hammoudeh Garcia <nadia.hammoudeh.garcia@ipa.fraunhofer.de>
| Status: Active
| Type: Tool
| Content-Type: text/x-rst
| Created: 15-April-2021

Abstract
========

This document summarizes different tools to easily and intuitively control actuators programmed with ROS drives and which use the common ros_control interfaces.

cob_script_server
=================

The cob_script_server is a python module that facilitates for the Care-O-bot robot the command of any command, it includes not only commands for actuators but also for other components like the face mimic or the sound interaction.


Code commands
-------------

The package cob_script_server offers an API for python apart of a console to command the instructions directly on a terminal.

The list of the available commands is the following:

============== ====================================================
Command        Function
============== ====================================================
init           initializes component
recover        recovers component after emergency stop
stop           stops current goal of component
move           move component to predefined joint configuration
move           move component to joint configuration
move           move component to predefined pose
move           move component to pose
move_base_rel  move relative pose base
say            says a predefined string 
say            says a string 
set_light      sets LEDs to a predefined or rgb color 
============== ====================================================

The complete documentation can be found under: http://wiki.ros.org/cob_script_server, also different use examples are available as a set of tutorials http://wiki.ros.org/cob_script_server/Tutorials.

Configuration
-------------

All the commmands can be easily configured by setting the appropiate parameters under the NameSpace "/script_server". The folder https://github.com/ipa320/cob_robots/tree/kinetic_dev/cob_default_robot_config/robots/cob4/script_server contains all the possible configurations for the script server for different types of components. For example for a 7 DOF manipulator it loooks:

+--------------------------------------------------------------------------------------------------------------------------------------------+
| joint_names: [arm_left_1_joint, arm_left_2_joint, arm_left_3_joint, arm_left_4_joint, arm_left_5_joint, arm_left_6_joint, arm_left_7_joint]|
| action_name: /arm_left/joint_trajectory_controller/follow_joint_trajectory                                                                 |
| service_ns: /arm_left/driver                                                                                                               |
| default_vel: 0.3                                                                                                                           |
|                                                                                                                                            |
| # single positions                                                                                                                         |
| home: [[0,0,0,0,0,0,0]]                                                                                                                    |
| folded: [[0.9599, 1.5708, -0.1200, 1.0000, 1.3800, 0.7500, -1.3600]]                                                                       |
| side: [[-0.9599, -1.6581, 1.0472, 1.6581, 1.0472, 0.6981, -1.0700]]                                                                        |
| ship: [[-1.57, -1.45, 1.57, 2.55, 0.0, -2.4, 0.0]]                                                                                         |
|                                                                                                                                            |
| hello1: [[-1.69,-1.19,0.48,2.09,0.34,-0.16,-0.12]]                                                                                         |
| hello2 : [[-1.69, -1.19, 0.48, 2.61, 0.34, 0.38, 0.5]]                                                                                     |
| arm_to_tray : [[1.06, 1.2, -1.4, 1.9, -1.84, -1.12, -0.64]]                                                                                |
|                                                                                                                                            |
| hello: [hello1, hello2, hello1, hello2, side]                                                                                              |
|                                                                                                                                            |
| wave1: [[-1.5, 0, 0, 0, 0, 0, 0]]                                                                                                          |
| wave2: [[-1.5, 0.3, 0, -1, 0, 0.7, 0]]                                                                                                     |
| wave3: [[-1.5, -0.3, 0, 1, 0, -0.7, 0]]                                                                                                    |
|                                                                                                                                            |
| wave_demo: [home,wave1,wave2,wave3,wave2,wave1,home,side]                                                                                  |
+--------------------------------------------------------------------------------------------------------------------------------------------+



Command GUI
-----------

To complete this tool there is a very easy to use GUI, which with a single click executes the different commands. The name of the package that includes this GUI is cob_command_gui (see http://wiki.ros.org/cob_command_gui).

The different group of buttons can be very easily configured using a yaml file, see an example under: https://github.com/ipa320/cob_robots/blob/kinetic_dev/cob_default_robot_config/robots/cob4-10/script_server/command_gui_buttons.yaml.

Motivation
==========

...

Rationale
=========

.....


Compatibility
=============

This tool was developed for ROS1. However, the python API module, should be easily ported to ROS2.


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

.. [#fhs] cob_script_server
   (http://wiki.ros.org/cob_script_server)

.. [#fhs] cob_command_gui
   (http://wiki.ros.org/cob_command_gui)

.. [#fhs] Source code
   (https://github.com/ipa320/cob_command_tools)

   
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

