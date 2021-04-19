Title: Upstart setup to automatically run a ROS system on boot 
Author: Nadia Hammoudeh Garcia <nadia.hammoudeh.garcia@ipa.fraunhofer.de>
Status: Active
Type: Tool
Content-Type: text/x-rst
Created: 15-April-2021

Abstract
========

This document provides a set of tools that can be used to create an upstart system for a robot.

Linux upstart configuration using services
==========================================

One of the most common linux tools to automatically start a service in boot is systemctl. To create your own service you must create a file that corresponds to the following format::

    [Unit]
    Description=my_script demo service
    After=network.target
    StartLimitIntervalSec=0

    [Service] 
    Type=simple 
    Restart=always 
    RestartSec=1 
    User=centos 
    ExecStart=/bin/bash my_script.sh

    [Install]
    WantedBy=multi-user.target

Where the user can define the command to be executed as start up job in the line "ExecStart". This files have saved with the suffix ".service" and copied to the folder "/etc/systemd/system/". Then the service can be enabled using the following command:

:code:`sudo systemctl enable ServiceName.service`

tmux tool
=============

tmux is an open-source terminal multiplexer for Unix-like operating systems. It allows multiple terminal sessions to be accessed simultaneously in a single window. It is useful for running more than one command-line program at the same time. It can also be used to detach processes from their controlling terminals, allowing remote sessions to remain active without being visible.

This tool has been used for the case of Care-O-bot to start automatically different launch files on the different computers and to be able to check the status of the started nodes during the execution. If this tool is not used, the programs would run in the background and would be very difficult to debug.

To facilitate the use and control of tmux sessions we create a script (found at https://github.com/ipa320/setup_cob4/blob/master/scripts/cob-command) with the following commands::

    Usage: cob-command command -options <arguments> 
        Commands:
           ls [-v] 
           find <session_name> 
           start [<file path>] 
           stop [-f] [-a|-u|<<session_name>] 
           stop_core shutdown 
           shutdown_slaves 
           reboot


To make it easier to start sessions this script uses as input a yaml file with the following format::

    roscore:
      session_name: roscore
      user: robot
      command: "roscore"
    bringup:
      session_name: bringup
      user: robot
      command: "roslaunch cob_bringup robot.launch"
      pre_condition: "until /opt/ros/myrosdistro/env.sh rostopic list; do sleep 1; done"


To enable it to start when booting the computer, just create a new service systemctl that uses "cob-command start path_to_yaml_file" as the start command.


Compatibility
=======================
These tools are independent of ROS and a specific distro, they are generic Linux.


Bugs and limitations
====================

?



References
==========

.. [#fhs] setup_con4 repository
   (https://github.com/ipa320/setup_cob4)

.. [#fhs] Tmux documentation
   (https://tmuxguide.readthedocs.io/en/latest/tmux/tmux.html)

.. [#fhs] Systemctl tutorial
   (https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6)
   
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

