| Title: How to set the ports of the hardware devices
| Author: Nadia Hammoudeh Garcia <nadia.hammoudeh.garcia@ipa.fraunhofer.de>
| Status: Active
| Type: Informational
| Content-Type: text/x-rst
| Created: 14-April-2021

Abstract
========

Whenever working with hardware, in addition to making sure that the drivers for the different ports are installed (in the case of linux, they are usually installed as standard with the operating system), we must make sure that each device is always under the same path for each new boot of the system and that users have read access to them. This is done using the udev rules.


Hardware setup
==============

udev rules
----------------

The first thing to do to define a new rule is to know the attributes that characterise your device. To do this, we connect it to an arbitrary port on our system and call the dmesg command to identify where it is mounted. Once located, we must give us access to it and call udevadm to give us its information, let's imagine that it corresponds to the port /dev/ttyUSB0:


:code:`sudo chmod 666 /dev/ttyUSB0`

:code:`sudo udevadm info -a -p $(udevadm info -q path -n /dev/ttyUSB0) > /tmp/usb0`


once we have located its characteristic information we create a new file with extension .rules that we must copy in the folder "/etc/udev/rules.d/". See https://wiki.archlinux.org/index.php/udev to help you with the syntax of this file format. 

For Care-O-bot you can find some examples in the folder: https://github.com/ipa320/setup_cob4/tree/master/udev_rules these are copied automatically during the installation. Besides that for the particular case of SICK S300 scanners, where the udev rules do not support the attributes that differentiate between two scanners of the same type, a script has been created and it will be called as part of the startup of the robot. This script will dynamically link between the port and the relative scanner name: https://github.com/ipa320/setup_cob4/blob/master/udev_rules/udev_cob.sh


Compatibility
=======================

Depending on the linux distro and its updated the instructions may change


Bugs and limitations
====================



Reference implementation
========================

Link to code and instructions avaiable under: https://github.com/ipa320/setup_cob4/blob/master/manual_administrator/README.asciidoc


References
==========

.. [#fhs] setup_cob4 repository
   (https://github.com/ipa320/setup_cob4)

.. [#fhs] setup general repository
   (https://github.com/ipa320/setup)
   
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

