# `Gentoo` Configuration

## Initial (temporary) configuration

The first step of the configuration is having a working system. We need to perform some basic configurations, just to be able to fully configure the system later on.

To have a working system, you need to do some temporary configuration: follow the [Temporary configuration](./temporary_configuration.md) tutorial.

## System configuration

It's time to fully configure your system.

Here it's not our focus to configure specific end-user software, but the base system, including:

1. Kernel.
2. Main daemons.
3. `Portage`.
4. `Layman`.

Follow the [Configurations install](./system_configuration.md) tutorial.

## Update packages

Now you should have new use flags, compiling options, etc.., so it's better to *recompile the entire system*.

```
$ emerge -e system
$ emerge -e world
```

## Install some basic packages

```ShellSession
$ emerge pciutils usbutils # To work with PCI & USB devices.
$ emerge parted # To manage partitions.
$ emerge layman gentoolkit genlop eix # Some nice portage utilities.
```

## Add overlays

```ShellSession
$ layman -a sunrise
```
