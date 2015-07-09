# NoMultiLib to Multilib

Sometimes you have a Gentoo system with a nomultilib profile and you need to
switch profile to multilib.

This operation is really difficult, more than it seems, because you need to
compile 32bit software, i.e. you need a 32bit compiler. But to have a 32bit
compiler you need to compile it, etc.. This is the *Chicken-and-egg problem*.

There are two way to perform the migration:

1. First of all, switch the profile to multilib (with `eselect`).
   Then, create a chroot environment with a multilib stage3 and compile the
   basic 32bit compiling toolchain; then pack those tools/libs, exit from chroot
   and install those binaries. Now you have the 32bit toolchain available and
   consider your system as multilib ready.
2. Install an already available 32bit toolchain with precompiled binaries
   directly in your system.

## Which method should I choose?

Imho method (1) is unnecessarily complicated.
**I suggest you to use method (2)**.

## Method (1)

It's described here:

- [jkroon's version](http://jkroon.blogs.uls.co.za/it/gentoo/gentoo-converting-no-multilib-to-multilib)
- [guymann's version](https://guymann.github.io/2013/02/11/32bit-gentoo/)

## Method (2)

- Install binaries for 32bit toolchain:

  ```ShellSession
  # PORTAGE_BINHOST="http://packages.gentooexperimental.org/packages/amd64-stable/" emerge -avG gcc glibc binutils libtool
  ```

- Select the compiler:

  ```ShellSession
  # gcc-config 1 # Replace 1 with the compiler you want.
  # source /etc/profile # Or open a new shell (maybe it's better).
  ```

- Reinstall the 32bit toolchain (source-based):

  ```ShellSession
  # emerge glibc libtool binutils coreutils
  # emerge gcc
  ```

- Re-emerge system:

  ```ShellSession
  # emerge -e system
  ```
