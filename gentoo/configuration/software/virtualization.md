# Virtualization

## `Virtualbox`

### Installation

```ShellSession
# emerge "sys-apps/usermode-utilities"
# emerge "app-emulation/virtualbox-bin"
# emerge "app-emulation/virtualbox-modules"
```

### Configuration

To be able to use `Virtualbox` with a normal user, you need to add it to the `vboxusers` group:

```ShellSession
# _username="alem0lars" # Replace with yours.
# gpasswd -a ${_username} vboxusers
```

## `Vagrant`

### Installation

```ShellSession
# emerge "app-emulation/vagrant"
```