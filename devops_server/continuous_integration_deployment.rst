Title: Continuous integration and deployment
Author: Ruichao Wu <ruichao.wu@ipa.fraunhofer.de>
Status: Active / Inactive
Type: Informational
Content-Type: text/x-rst
Created: 16-April-2021

Abstract
========

Continuous integration and deployment tools for ROS1

Continuous Integration
==============================================
Buildbot-ros (https://github.com/mikeferguson/buildbot-ros) mainly developed by Michael Ferguson 
is to build ROS1 packages, run continuous integration testing, and build docs.

* Advantages:

    * Support private repositories

* Disadvantage: 

    * Using cowbuilder

There are two tools developed base Buildbot-squirrel. 
One is Buildbot-squirrel, another is ros-buildbot-docker.


Buildbot-squirrel 
---------------------------------------------------------------------

Buildbot-squirrel (https://github.com/buildbot-squirrel/buildbot-ros) support private ROS distro,
add hook

ROS-Buildbot-Docker
---------------------
Improvements:

* Using a docker container as a building environment instead of using cowbuilder.
* Releasing debian packages in a local repositories after building debian packages successfully.
* Updating rosdep after building debian packages successfully. So that rosdep can find dependencies for other packages.

Issues:

*  

1. Setup:
.........

1. Install docker

2. gpg key setting (for releasing packages in a local repository)

3. start

    :code:`sh start.bash` 

2. Configrations
................

1. Buildbot master config:

2. ROS private distro config:

3. Docker image config (for running test)

4. Loacl repositories setting (nginx)

Industrial CI
---------------------

Continuous Deployment
=====================

Docker containers
--------------------------------

https://github.com/reapp-project/reapp_ipde


Debian packages
----------------

Snaps
-------

Motivation
==========


Rationale
=========


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

.. [#fhs] Buildbot-ros 
    (https://github.com/mikeferguson/buildbot-ros)

.. [#fhs] Industrial CI
   (https://github.com/ros-industrial/industrial_ci)

.. [#fhs] Packaging your ROS project as a snap
    (http://wiki.ros.org/ROS/Tutorials/Packaging%20your%20ROS%20project%20as%20a%20snap)
   
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

