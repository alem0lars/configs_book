# Gentoo Configuration

## Initial (temporary) configuration

The first step of the configuration is having a working system. We need to
perform some basic configurations, just to be able to fully configure the
system later on.

To have a working system, you need to do some temporary configuration: follow
the [Temporary configuration](./temporary_configuration.md) tutorial.

## System configuration

It's time to fully configure your system.

Here it's not our focus to configure specific end-user software, but the
base system, including:

1. Kernel.
2. Main daemons.
3. Portage.
4. Layman.
5. Display manager
6. Window manager
7. etc... (as much as you can)

Follow the
[Configurations install](./system_configuration.md)
tutorial.

## Additional hardware support

For every additional hardware (not supported by default), follow the
corresponding guide. The available ones are listed [here](./device_specific).

## Build the kernel

Now the kernel is configured (i.e. the `.config` file has been copied to
`/usr/src/linux`).
We need to rebuild it to use the new configurations.

Mount the EFI partition under `/boot` and run the following:

```ShellSession
# _dst_kernel_image="/boot/EFI/gentoo/kernel-hardened-latest.efi"
# cd "/usr/src/linux"
# make && make modules_install
# cp "arch/x86_64/boot/bzImage" "${_dst_kernel_image}"
```

### Start and enable Systemd-Networkd

```ShellSession
# systemctl enable "systemd-networkd"
# systemctl start "systemd-networkd"
```

### Start and enable Systemd-Resolved

```ShellSession
# systemctl enable "systemd-resolved"
# systemctl start "systemd-resolved"
# ln -sf /run/systemd/resolve/resolv.conf /etc/resolv.conf
```

### Start and enable `Avahi`

```ShellSession
# systemctl enable "avahi-daemon"
# systemctl start "avahi-daemon"
```

## Local portage overlay

Create it running:

```ShellSession
# mkdir -p /usr/local/portage/{metadata,profiles}
# echo 'local' > /usr/local/portage/profiles/repo_name
# echo 'masters = gentoo' > /usr/local/portage/metadata/layout.conf
# chown -R portage:portage /usr/local/portage
```

Next, tell portage about the overlay.

## Update packages

Now you should have new use flags, compiling options, etc.., so it's better
to *recompile the entire system*.

```
# emerge -e "system"
# emerge -e "world"
```

## Install daemons

```ShellSession
# emerge "wpa_supplicant"
```

## Install some basic packages

```ShellSession
# emerge pciutils usbutils # To work with `PCI `& `USB` devices.
# emerge parted # To manage partitions.
# emerge gentoolkit genlop eix # Some nice `portage` utilities.
# emerge "sys-apps/gentoo-functions"
# emerge "dev-util/debugedit"
# emerge "sys-fs/ntfs3g"
```

## Install Layman

Install Layman:

```ShellSession
# emerge "app-portage/layman"
```

Remove and regenerate old cache:

```ShellSession
# rm -rf "/var/cache/edb/dep"
# emerge --metadata
# eix-update
# eix-sync
```

## Install X stack

```ShellSession
# emerge "x11-apps/xrandr" "x11-apps/xdpyinfo"
# emerge "setxkbmap" "xmodmap" "x11-apps/xinput" "xbacklight"
# emerge "xorg-server"
# emerge "x11-misc/lightdm"
# systemctl enable lightdm
```

## Install window manager

```ShellSession
# emerge "x11-wm/awesome"
```

## Install other software

```ShellSession
# emerge "app-admin/sudo"
# emerge "app-shells/zsh"
# emerge "media-gfx/feh"
# emerge "media-sound/pavucontrol"
# emerge "x11-misc/xclip" "x11-misc/xsel"
# emerge "x11-terms/rxvt-unicode" "x11-misc/urxvt-perls"
```

## Install fonts

```ShellSession
# emerge "media-fonts/powerline-fonts"
```

## Install chips

Install all of the following [chips](https://github.com/alem0lars/chips):

* [GNU/Linux](https://github.com/alem0lars/chips/tree/master/scripts/gnulinux):
  General purpose scripts for GNU/Linux scripts.
* [Gentoo](https://github.com/alem0lars/chips/tree/master/scripts/gentoo):
  Scripts specific for Gentoo systems.

## Setup device-specific software

Sometimes you need to install (and configure) software specific to a
particular device.

The main example is installing drivers..

[Here](./device_specific) is a list of device-specific software setup
tutorials.

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
$ echo "%admin ALL=(ALL) ALL" > "/etc/sudoers.d/group-admin"
$ chmod 600 "/etc/sudoers.d/group-admin"
```

Finally, add the `ssh` keys for the created user.

## User-level configuration

If you are using Fizzy, that's simple:

```ShellSession
$ _username="alem0lars" # Replace with yours.
$ _vars_name="julia_hck_gentoo" # Replace with yours.
$ _meta_name="meta-user.yml" # Replace with yours.
$ fizzy cfg instantiate --vars-name=${_vars_name} --inst-name="user_${_username}"
$ fizzy sys install --vars-name=${vars_name} --inst-name="user-${_username}" --meta-name="${_meta_name}"
```

You may want to run the snippet above for every user you want to be configured in your system.
I personally run this for alem0lars and root.

## (Optional) Configure data

See [here](./data_configuration.md).

## Install additional software

* [Backup](./software/backup.md)
* [Web clients](./software/web_clients.md)
* [Mail](./software/mail.md)
* [RSS](./software/rss.md)
* [IRC](./software/irc.md)
* [Twitter](./software/twitter.md)
* [FTP](./software/ftp.md)
* [Torrent](./software/torrent.md)
* [Usenet](./software/usenet.md)
* [Files management](./software/files_management.md)
* [Files sharing](./software/files_sharing.md)
* [Images tools](./software/images_tools.md)
* [Images viewers](./software/images_viewers.md)
* [Images editors](./software/images_editors.md)
* [GTD](./software/gtd.md)
* [Prototyping](./software/prototyping.md)
* [Diagram tools](./software/diagram_tools.md)
* [Audio player](./software/audio_player.md)
* [Video player](./software/video_player.md)
* [Office](./software/office.md)
* [Math](./software/math.md)
* [Signal processing](./software/signal_processing.md)
* [Documents viewers](./software/docs_viewers.md)
* [Text editors](./software/text_editors.md)
* [PaaS tools](./software/paas_tools.md)
* [IDE](./software/ide.md)
* [Semantic tools](./software/semantic_tools.md)
* [VCS](./software/vcs.md)
* [Development tools](./software/dev_tools.md)
* [Electronics](./software/electronics.md)
* [Debuggers](./software/debuggers.md)
* [Fuzzers](./software/fuzzers.md)
* [ELF tools](./software/elf_tools.md)
* [Carving](./software/carving.md)
* [Network analyzers](./software/net_analyzers.md)
* [Network tools](./software/net_tools.md)
* [Password cracking](./software/password_cracking.md)
* [System monitoring](./software/sysmon.md)
* [Clipboard](./software/clipboard.md)
* [Password manager](./software/password_manager.md)
* [Miscellaneous](./software/misc.md)
* [Accounting](./software/accounting.md)
* [GTD](./software/gtd.md)
* [Screencasts](./software/screencasts.md)
* [Screen sharing](./software/screen_sharing.md)
* [Docs](./software/docs.md)
* [Flashcards](./software/flashcards.md)
* [Cross compile](./software/cross_compile.md)
* [C](./software/c.md)
* [D](./software/dlang.md)
* [Android](./software/android.md)
* [JVM](./software/jvm.md)
* [JSON](./software/json.md)
* [Haskell](./software/haskell.md)
* [NodeJS](./software/nodejs.md)
* [Perl](./software/perl.md)
* [Python](./software/python.md)
* [Ruby](./software/ruby.md)
* [R](./software/r.md)
* [TeXlive](./software/texlive.md)
* [ctags](./software/ctags.md)
* [Socat](./software/socat.md)
* [sqlmap](./software/sqlmap.md)
* [Virtualization](./software/virtualization.md)
* [Log tools](./software/log_tools.md)
* [Terminal multiplexer](./software/terminal_multiplexer.md)
* [Calc](./software/calc.md)
* [Mumble](./software/mumble.md)

## Fonts setup

See [here](./fonts.md).
