# Virtualization

## Virtualbox

```ShellSession
# emerge "sys-apps/usermode-utilities"
# emerge "app-emulation/virtualbox-bin"
# emerge "app-emulation/virtualbox-modules"
```

### Configuration

To be able to use Virtualbox with a normal user, you need to add it to
the `vboxusers` group:

```ShellSession
# gpasswd -a "alem0lars" "vboxusers" # Replace with yours.
```

### Notes

You can store virtual machines in an external hard-drive (like me).

A good mount-point for the external hard-drive is: `/vm`.
In that case, prior to use virtual machines you'll need to mount it:

```ShellSession
# mount "${_dev_path}" "/dev/sdb1" # Replace with yours.
```

## Vagrant

```ShellSession
# emerge "app-emulation/vagrant"
```

### Plugins

```ShellSession
# vagrant plugin install vagrant-windows # Remove when updated to Vagrant 1.6+
```

### Notes

You can store boxes, as well as normal virtual machines, in an external
hard-drive (like me).

A good mount-point for the external hard-drive is: `/vm`.
A good directory used to store the vagrant boxes is then: `/vm/vagrant/boxes`

In order to do that, mount the hard-drive to `/vm` and run:

```ShellSession
# mkdir -p /vm/vagrant/boxes
# ln -s /vm/vagrant/boxes ~/.vagrant.d/boxes # For every user using vagrant.
```

When you want to use vagrant, remember to mount the hard-drive storing the
boxing:

```ShellSession
# _dev_path="/dev/sdb1" # Replace with yours.
# mount "${_dev_path}" "/vm"
```

## KVM

```ShellSession
# emerge "app-emulation/qemu"
# gpasswd -a ${_username} kvm # Replace ${_username} with who can access VMs.
```

### Prerequisites

Ensure your kernel is correctly configured (see
[here](https://wiki.gentoo.org/wiki/QEMU)).
