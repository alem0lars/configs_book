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

## Build the kernel

Now the kernel is configured (i.e. the `.config` file has been copied to `/usr/src/linux`).
We need to rebuild it to use the new configurations.

Mount the `EFI` partition under `/boot` and run the following:

```ShellSession
$ _dst_kernel_image="/boot/EFI/gentoo/kernel-hardened-latest.efi"
$ cd "/usr/src/linux"
$ make && make modules_install
$ cp "arch/x86_64/boot/bzImage" "${_dst_kernel_image}"
```

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

## Install daemons

```ShellSession
$ emerge wpa_supplicant
```

## Install some basic packages

```ShellSession
$ emerge pciutils usbutils # To work with `PCI `& `USB` devices.
$ emerge parted # To manage partitions.
$ emerge gentoolkit genlop eix # Some nice `portage` utilities.
$ emerge nmap # You may need nmap for file transfers (`ncat`).
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
$ emerge x11-apps/xrandr x11-apps/xdpyinfo setxkbmap xmodmap x11-apps/xinput xorg-server
$ emerge xmonad xmonad-contrib
$ emerge x11-misc/slim
$ systemctl enable slim
```

## Install other software

```ShellSession
$ emerge app-admin/sudo
$ emerge app-admin/conky
$ emerge app-misc/tmux
$ emerge app-shells/zsh
$ emerge media-gfx/feh
$ emerge media-sound/pavucontrol
$ emerge x11-misc/dzen
$ emerge x11-misc/dmenu
$ emerge x11-misc/xclip x11-misc/xsel x11-misc/autocutsel x11-misc/parcellite
$ emerge x11-misc/trayer-srg
$ emerge x11-terms/rxvt-unicode x11-misc/urxvt-perls
$ emerge x11-themes/FlatStudio # GTK 2/3 theme.
```

## Install fonts

```ShellSession
$ emerge powerline-fonts
```

## Install `chips`

Install all of the following [`chips`](https://github.com/alem0lars/chips):

* [`GNU/Linux`](https://github.com/alem0lars/chips/tree/master/scripts/gnulinux): General purpose scripts for `GNU/Linux` scripts.
* [`Gentoo`](https://github.com/alem0lars/chips/tree/master/scripts/gentoo): Scripts specific for `Gentoo` systems. 

## Setup device-specific software

Sometimes you need to install (and configure) software specific to a particular device.

The main example is installing drivers..

[Here](./device_specific) is a list of device-specific software setup tutorials.

## Create your personal user

```ShellSession
$ _comment="Personal user for Alessandro Molari" # Replace with yours.
$ _username="alem0lars" # Replace with yours.
$ useradd -d "/home/${_username}" -s /bin/zsh -c "${_comment}" -m "${_username}"
```

Create the administrators group:

```ShellSession
$ groupadd admin
```

Add your user to groups:

```ShellSession
$ _username="alem0lars" # Replace with yours.
$ gpasswd -a ${_username} admin
$ gpasswd -a ${_username} portage
```

Now allow `admin` to user `sudo`:

```ShellSession
$ echo "%admin ALL=(ALL) ALL" > "/etc/sudoers.d/group_admin"
$ chmod 600 "/etc/sudoers.d/group_admin"
```

Finally, add the `ssh` keys for the created user.

## User-level configuration

If you are using `Fizzy`, that's simple:

```ShellSession
$ _username="alem0lars" # Replace with yours.
$ fizzy cfg instantiate --vars-name=julia_hck_gentoo --inst-name="user_${_username}"
$ fizzy sys install --vars-name=julia_hck_gentoo --inst-name="user_${_username}"
```

*Answer no when `Fizzy` will ask you if you want to overwrite system files* (like files in `/etc`) because they should belong to the `system` instance.

## (Optional) Configure `archive`

See [here](./archive_configuration.md)

## Install additional software

* [Files management](./software/files_management.md)
* [Images editors](./software/images_editors.md)
* [Text editors](./software/text_editors.md)
* [Web browsers](./software/web_browsers.md)
* [VCS](./software/vcs.md)
* [`Java`](./software/java.md)
* [`Perl`](./software/perl.md)
* [`TeXlive`](./software/texlive.md)
* [`ctags`](./software/ctags.md)
* [IRC client](./software/irc_client.md)
* [Network Analyzers](./software/net_analyzers.md)
* [Fuzzers](./software/fuzzers.md)
* [Hex editor](./software/hex_editor.md)
* [Docs](./software/docs.md)
* [`FTP`](./software/ftp.md)
* [System monitoring](./software/sysmon.md)
* [`Socat`](./software/socat.md)
