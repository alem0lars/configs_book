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

## KVM

```ShellSession
# emerge "app-emulation/qemu"
# gpasswd -a ${_username} kvm # Replace ${_username} with who can access VMs.
```

### Prerequisites

Ensure your kernel is correctly configured (see
[here](https://wiki.gentoo.org/wiki/QEMU)).
