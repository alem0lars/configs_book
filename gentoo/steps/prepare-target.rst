Prepare target
==============

The target environment needs to be prepared, this entails:

1. **Booting to a Gentoo minimal disk**
2. **Ensuring that there's networking available**
3. **Setting a root password**
4. **Enabling SSH**

Step 1: Boot
============

Insert the Gentoo live-cd (or live-usb or whatever) and boot it.

In the boot prompt just press ``<enter>`` if you don't need any particular boot
argument; otherwise, this_ is the list of some boot options.

.. _this:
  https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Media#Booting_the_CD

Step 2: Ensure that there's networking available
================================================

First of all, the networking may already work properly. Check it by running:

.. code-block:: shell-session

  # ping "www.google.com"
  # ping "${_WORKSTATION_IP}"

In the line above we've assumed  the IP address of the ``workstation``,
which needs to be reachable in order to complete the installation, is stored
inside the environment variable ``_WORKSTATION_IP``, i.e. it can be accessed
using ``${_WORKSTATION_IP}``.

If network is unreachable and you use a DHCP server, try to restart it:

.. code-block:: shell-session

  # kill $(ps aux | grep dhcpcd | grep -v grep | awk '{print $2}')
  # /etc/init.d/dhcpcd restart
  * Stopping DHCP Client Daemon ...
  * Starting DHCP Client Daemon ...

If you don't use a DHCP server, you need to setup your network manually.

For more informations take a look at the `Gentoo Handbook`_.

.. _`Gentoo Handbook`:
  https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Networking

Step 3: Set root password
=========================

To change the password for the ``root`` user, run:

.. code-block:: shell-session

  # passwd
  New password:
  Retype new password:
  passwd: password updated successfully

Step 4: Enable SSH
==================

SSH is disabled by default, but it needs to be enabled so the ``workstation``
can remotely reach the ``target``.

To enable SSH, run:

.. code-block:: shell-session

  # /etc/init.d/sshd start
  ssh-keygen: generating new host keys: RSA DSA ED25519
  * Starting sshd ...

.. raw:: html

  <embed><hr></embed>

Congratulations, now the ``target`` is prepared.

The next step is to `Install the OS`_.

.. _`Install the OS`: ./install-os.rst
