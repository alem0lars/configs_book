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
5. Display manager
6. Window manager
7. etc... (as much as you can)

Follow the [Configurations install](./system_configuration.md) tutorial.

### Start and enable `networkd`

```ShellSession
$ systemctl enable systemd-networkd
$ systemctl start systemd-networkd
$ systemctl enable systemd-resolved
$ systemctl start systemd-resolved
$ ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

### Start and enable `resolved`

```ShellSession
$ systemctl enable systemd-resolved
$ systemctl start systemd-resolved
$ ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

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
$ emerge gentoolkit genlop eix # Some nice portage utilities.
$ emerge nmap
```

## Install `layman`

Install `layman`:

```ShellSession
$ emerge layman
```

Remove and regenerate old cache:

```ShellSession
$ rm -rf /var/cache/edb/dep 
$ emerge --metadata
$ eix-sync
```

## Install `X` stack

```ShellSession
$ emerge x11-apps/xrandr x11-apps/xdpyinfo setxkbmap xmodmap xorg-server
$ emerge xmonad xmonad-contrib
$ emerge x11-misc/slim
$ systemctl enable slim
```

## Install other software

```ShellSession
$ emerge x11-misc/dzen
$ emerge x11-terms/rxvt-unicode x11-misc/urxvt-perls
$ emerge x11-misc/trayer-srg
$ emerge media-gfx/feh
$ emerge app-admin/conky
$ emerge x11-misc/dmenu
$ emerge x11-misc/xclip x11-misc/autocutsel x11-misc/parcellite
$ emerge app-shells/zsh
$ emerge app-misc/tmux
```

## Install fonts

```ShellSession
$ emerge powerline-fonts
```

## Install `chips`

Install all of the following [`chips`](https://github.com/alem0lars/chips):

* [`GNU/Linux`](https://github.com/alem0lars/chips/tree/master/scripts/gnulinux): General purpose scripts for `GNU/Linux` scripts.
* [`Gentoo`](https://github.com/alem0lars/chips/tree/master/scripts/gentoo): Scripts specific for `Gentoo` systems. 
