| Title: How to install automatically a distributed robot system with several PCS
| Author: Nadia Hammoudeh Garcia <nadia.hammoudeh.garcia@ipa.fraunhofer.de>
| Status: Active
| Type: Informational
| Content-Type: text/x-rst
| Created: 14-April-2021

Abstract
========

The structure f this type of system is relatively complex as it has to fulfil the particularity of the synchronous installation of all the computers so that they can communicate with each other and share the /home folder, so that the user accounts are exactly the same on all of them.


NFS and NTP setup
=================

Network File System (NFS) is a distributed file system protocol that allows an user on a client computer to access files over a computer network much like local storage is accessed. For the case of a robot with several computers, this is very usefull to have a single shared home directory accesable from all the computers.

NFS requires a robust and stable network setup, in conjunction with the ssh configuration and the syncronization os the time (using for example NTP).

Network configuration
---------------------

To ensure a fast and stable connection the use of a router with dedicated static IP addresses is strongly recommended. Apart of that for case of linux we suggest to define also the full list of computers of the network as a pair: hostname - IP address in the file :code:`/etc/hosts`.



Setup NFS Server
----------------


Install the NFS server package and create the NFS directory (we will create a /u directory to be shared):

:code:`sudo apt-get install nfs-kernel-server`
:code:`sudo mkdir /u`

Add the following line to /etc/fstab to mount /u as /home directory:

:code:`/home /u none bind 0 0`

Mount the drive

:code:`sudo mount /u`

Activate STATD in /etc/default/nfs-common by changing th NEED_STATD to yes

:code:`NEED_STADT=yes`

Add the following line to /etc/exports:

:code:`/u *(rw,fsid=0,sync,no_subtree_check)`

Change the home directory of the robot user from /home/robot to /u/robot in the /etc/passwd file.

After finishing you need to reboot the pc

:code:`sudo reboot`


Setup NFS Clients
-----------------

Install the NFS client package and create the NFS directory

:code:`sudo apt-get install nfs-kernel-server autofs`
:code:`sudo mkdir /u`

Activate STATD in /etc/default/nfs-common by changing the NEED_STATD to yes

:code:`NEED_STATD=yes`

Edit /etc/auto.master and add

:code:`/-  /etc/auto.direct`

Create a new file /etc/auto.direct with the following line, IP is the parameter that define your robot network:

:code:`/u  -fstype=nfs4    server_IP:/`

Activate the NFS

:code:`sudo update-rc.d autofs defaults`
:code:`sudo service autofs restart`
:code:`sudo modprobe nfs`

Change the home directory of the robot user from /home/robot to /u/robot in the /etc/passwd file.

After finishing you need to reboot the pc

:code:`sudo reboot`



Enable passwordless login
-------------------------

Enable passwordless login to all robot pcs for robot user, from the server PC call the following commands:

:code:`ssh-keygen`
:code:`ssh-copy-id hostname_server_IP`
:code:`ssh hostname_client_IP`



Setup NTP time synchronitation
------------------------------

Install the ntp package

:code:`sudo apt-get install ntp`

On the server PC add the following lines to the file :code:`/etc/ntp.conf`:

:code:`server 0.pool.ntp.org`
:code:`restrict 10.4.X.0 mask 255.255.255.0 nomodify notrap`

and for the client side:


:code:`server 10.4.X.11`


Motivation
==========

Unify the setup of the filesystem directory and its access


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

