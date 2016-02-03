Introduction
============

Gentoo installation and configuration using Ansible.

This guide assumes you already have a *working machine, allowed to remotely
connect* to the machine you're going to install Gentoo.

From now on, the following naming conventions will be used:

- ``target``: the machine where Gentoo's going to be setup.
- ``workstation``: the machine connected to the ``target`` which performs the
  setup, executing remote commands.

Requirements
============

The ``workstation`` needs to have Ansible installed.
If you need help, consult the `Official installation guide`_.

Steps
=====

+---+-----------------------------------------+-------------------+
| N | Description                             | Guide             |
+===+=========================================+===================+
| 1 | Prepare ``target`` for installation:    | `Prepare target`_ |
|   | boot live and make it reachable.        |                   |
+---+-----------------------------------------+-------------------+
| 2 | Perform remote Gentoo installation      | `Install the OS`_ |
|   | from ``workstation`` to ``target``.     |                   |
+---+-----------------------------------------+-------------------+
| 3 | Setup ``target``'s OS, including        | Configure_        |
|   | software installation and configuration |                   |
+---+-----------------------------------------+-------------------+

.. _`Official installation guide`:
  http://docs.ansible.com/ansible/intro_installation.html
.. _`Prepare target`:
  ./steps/prepare-target.rst
.. _`Install the OS`:
  ./steps/install-os.rst
.. _Configure:
  ./steps/configure.rst
