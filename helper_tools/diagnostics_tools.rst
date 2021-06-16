| Title: Tools to diagnosse and monitor a system
| Author: Nadia Hammoudeh Garcia <nadia.hammoudeh.garcia@ipa.fraunhofer.de>
| Status: Active
| Type: Tool
| Content-Type: text/x-rst
| Created: 15-April-2021

Abstract
========

This document summarizes different tools to easily monitor and diagnosse ROS systems

diagnostics
============

The diagnostics system is designed to collect information from hardware drivers and robot hardware to users and operators for analysis, troubleshooting, and logging. The diagnostics stack contains tools for collecting, publishing, analyzing and viewing diagnostics data.

The diagnostics toolchain is built around the global topic /diagnostics. The diagnostic_updater and self_test packages allow nodes to collect and publish diagnostics data. The diagnostic_aggregator can categorize and analyze diagnostics at runtime. Operators and developers can view the diagnostics data using the rqt_robot_monitor package. The diagnostic_analysis package can convert diagnostics logs to CSV files for examination and after-the-fact analysis. 

this package can be considered the standard ROS monitoring package. Being the diagnostic_msgs/DiagnosticArray interface the recommended common one to publish the status of the components during the execution of the application.

Link: http://wiki.ros.org/diagnostics

cob_monitoring
=============

the cob_monitoring package includes a series of python scripts for monitoring the system on which the software is running. Among the aspects it covers are:

- Robot's battery (battery_monitor.py )
- CPU usage of each computer (cpu_monitor.py)
- memory usage of each computer (hd_monitor.py)
- monitoring of topical publishing frequency (hz_monitor.py)
- Monitoring of the network (net_monitor.py, wlan_monitor.py , wifi_monitor.py)
- Time synchronisation between computers (ntp_monitor.py)
- Robot emergency (emergency_stop_monitor.py)

All these scripts are generic, can be configured using a yaml file and publish the standard ROS diagnostic message diagnostic_msgs/DiagnosticArray http://docs.ros.org/en/api/diagnostic_msgs/html/msg/DiagnosticArray.html allowing the use of all the tools in the diagnotics package (http://wiki.ros.org/diagnostics).

Link: https://github.com/ipa320/cob_command_tools/tree/indigo_dev/cob_monitoring

rosgraph_monitor
=============

`rosgraph_monitor` is a runtime monitoring tool, which can be used to create observers to monitor different aspects of a running ROS system. This tool is directly linked to [ROS models](https://github.com/ipa320/ros-model).  
`ROSGraphObserver` is an observer available by default. It generates a `RosSystem` model by taking a snapshot of the ROS graph, which is compared with the desired `RosSystem` model of base application. It publishes a diagnostic error message in case a difference is detected.
Other "property observers" can be created with custom logic to monitor sensitive properties during runtime. The scripts that are part of this package are:

- main script to load / unload the available observers (`monitor`)
- create and dump `RosSystem` snapshot of running ROS system (`rossystem_snapshot`)

Link: https://github.com/ipa320/rosgraph_monitor

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

The monitoring software was developed for ROS1.



Bugs and limitations
====================



References
==========

.. [#fhs] cob_monitoring
   (https://github.com/ipa320/cob_command_tools/tree/indigo_dev/cob_monitoring)

.. [#fhs] ROS diagnotics
   (http://wiki.ros.org/diagnostics)

.. [#fhs] ROSgraph monitor
   (https://github.com/ipa320/rosgraph_monitor)
   
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

