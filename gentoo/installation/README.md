# `Gentoo` Installation

## Requirements

You'll need Internet connectivity.

## Boot installer

Boot the installer, which is any live `GNU/Linux`.

Check if you can reach Internet (e.g. `ping 8.8.8.8`) and if your `DNS` setup is correct (e.g. `ping www.google.com`).

## Partitioning

### Initial informations

Here you have many choices:

1. Create LVM based partitioning layout
2. Create "normal" partitions, without any logical volume management.

In any case, you'll need the following partitions:

1. `root` partition:
  * It will be mounted in `/`.
  * Suggested filesystem: `ext4`.

2. `swap` partition:
  * It will be serve as swapping space.

3. `boot` partition:
  * Holds bootloader informations.
  * You shouldn't have this partition if you have a `UEFI` system.
  * If you haven't an `UEFI` system this partition is *optional*: you can have the `/boot` directory inside the `root` partition instead of having a separate partition. However, creating a separate partition is always preferred.

4. `efi` partition:
  * Holds informations used by the boot-manager and boot-loaders.
  * If you're doing a dualboot setup with `OSX` you already have this partition.

5. `tmp` partition:
  * It will be mounted in `/`.
  * This partition is *optional*: you can have the `/tmp` directory inside the `root` partition or mounted in `RAM`. In that cases you shouldn't have this partition. If you have enough RAM for `/tmp` (it depends, but IMHO `8GB` is enough), then the `RAM` method is preferred.

Of course you can add as many partitions as you want but keep in mind you should create a new partition only if you have a really valid reason to do that, because many partitions have it's drawbacks (resizing partitions is a delicate task).

#### Additional resources

If doing a `GNU/Linux`-`OSX` dualboot setup, then read its dedicate [partitioning suggestions](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#partitioning-suggestions).

### Create partitions

#### With `LVM`

TODO

#### Without `LVM`

Open `parted` (the partitioning tool of choice):

```ShellSession
$ _dev_name="/dev/sda" # Replace with the path of your disk device.
$ parted -a optimal "${_dev_name}"
$ unit mib # Set MiB as the default unit (the unit to use when no one is specified).
```

For each partition you want to create, do the following:

```ShellSession
(parted) mkpart primary <FILESYSTEM> <START> <END>
```

where:

* `<FILESYSTEM>`: replace with the filesystem you want to use for that partition (e.g. `ext4`, `linux-swap`, etc..).
* `<START>`: the first byte to use. It's the `End` of the previous partition (you can see it with the command `print`) *plus `1MiB`* which is `1` because the current default unit is `MiB`, for aligning the partitions correctly.
* `<END>`: the last byte to use. You can calculate it as `<START> + <SIZE>` where `<SIZE>` is the size you want to give at the partition.

Assign a name to the created partition:

```ShellSession
(parted) name <NUMBER> <NAME>
```

where:

* `<NUMBER>`: is the partition number. It identifies which partition you want to give the name to.
* `<NAME>`: the name to assign to the created partition.

### Format the partitions

Every partition you've created should be formatted. The command depends on the filesystem:

* `ext4`:
  
  ```ShellSession
  $ _dev_path="/dev/sda5" # Replace with your path.
  $ mkfs.ext4 "${_dev_path}"
  ```
  
* `swap`:

  ```ShellSession
  $ _dev_path="/dev/sda4" # Replace with your path.
  $ mkswap "${_dev_path}"
  ```

### Mount the partitions

```ShellSession
$ _swap_dev_path="/dev/sda4" # Replace with your swap path.
$ _root_dev_path="/dev/sda5" # Replace with your root path.
$ swapon "${_swap_dev_path}"
$ mkdir "/mnt/gentoo"
$ mount "${_root_dev_path}" "/mnt/gentoo"
```

Of course for any additional partition you have you should create the directory (relative to the root path) and mount the partition into it. For example if you have a `var` partition in `/dev/sda7`, then you've done: `mkdir /mnt/var  && mount /dev/sda7 /mnt/gentoo/var`.

## Check the date is correct

([Stolen from gentoo handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64/Full/Installation), ty :D)

Before installing Gentoo, make sure that the date and time are set correctly. A mis-configured clock may lead to strange results in the future!

To verify the current date/time, run date:

```ShellSession
$ date
Fri Mar 29 16:21:18 UTC 2005
```

If the date/time displayed is wrong, update it using the date `MMDDhhmmYYYY` syntax (Month, Day, hour, minute and Year). At this stage, it is recommended to use `UTC` time. Later on during the installation, the timezone will be defined.

For instance, to set the date to `March 29th, 16:21` in the year `2014`:

```ShellSession
$ date 032916212014
```

## Download installation files

Download the `stage3` from [http://www.gentoo.org/main/en/mirrors.xml](http://www.gentoo.org/main/en/mirrors.xml)  (it's located inside the directory `releases/amd64/autobuilds`).

and save them to the installation root mount directory (e.g. `/mnt/gentoo`).

## Install `stage3`

Go to the installation root mount directory and extract the downloaded `stage3` archive:

```ShellSession
$ _root_dir="/mnt/gentoo"
$ cd "${_root_dir}"
$ tar xvjpf stage3-*.tar.bz2
```

## Before `chroot`

### Set options

Before installing other packages you should (temporarly) set some configurations.
Later we will set them better but now we just need to be able to install `Gentoo`, nothing more.

Edit the file `make.conf`:

```ShellSession
$ _root_dir="/mnt/gentoo"
$ nano "${_root_dir}/etc/portage/make.conf"
```

And perform the following changes:

* Set `CFLAGS` to `-march=native -O2 -pipe`
* Set `MAKEOPTS` to `-j<X>` where `<X>` is the cores count + 1.
* Set `SYNC` to `rsync://rsync.de.gentoo.org/gentoo-portage` (maybe replace with some ones near you).

### Save `DNS` informations

Copy `DNS` informations from the live system:

```ShellSession
$ _root_dir="/mnt/gentoo"
$ cp -L /etc/resolv.conf "${_root_dir}/etc/"
```

## Perform `chroot`

To make sure that the new environment works properly, certain filesystems need to be made available there as well:

```ShellSession
$ _root_dir="/mnt/gentoo"
$ mount -t proc proc "${_root_dir}/proc"
$ mount --rbind /sys "${_root_dir}/sys"
$ mount --make-rslave "${_root_dir}/sys"
$ mount --rbind /dev "${_root_dir}/dev"
$ mount --make-rslave "${_root_dir}/dev"
$ chroot "${_root_dir}" /bin/bash
$ source /etc/profile
$ export PS1="(chroot) $PS1"
```

### Notes

([Stolen from gentoo handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64/Full/Installation), ty :D)

When using non-`Gentoo` installation media, this might not be sufficient. Some distributions make `/dev/shm` a symbolic link to `/run/shm/` which, after the `chroot`, becomes invalid.
Making `/dev/shm/` a proper `tmpfs` mount up front can fix this:

```ShellSession
$ rm /dev/shm && mkdir /dev/shm
$ mount -t tmpfs -o nosuid,nodev,noexec shm /dev/shm
```

Also ensure that mode `1777` is set:

```ShellSession
$ chmod 1777 /dev/shm
```

## Install `portage`

```ShellSession
$ emerge-webrsync
$ emerge --sync
```

## Set the right profile

I suggest you to use the `hardened` and `no-multilib` profile. It should appear as something like
`[14] hardened/linux/amd64/no-multilib`.

```
$ eselect profile list # Will list all of the available profiles.
$ eselect profile set <X> # Will set the profile to <X>
```

## Install `systemd`

* Add `systemd` to your useflags.
* Then run emerge, so packages relying upon `systemd` will be aware of the useflag:

  ```ShellSession
  $ emerge -avDN @world
  ```

### Notes

If you get dependency problems (`sys-fs/udev` is blocking `sys-apps/systemd`), `sys-fs/udev` may be in the world file and it shouldn't be there because it's included inside `systemd`.
Try to resolve this by:

```ShellSession
$ emerge --deselect sys-fs/udev
```

## Set some basic system-wide informations

Set the hostname:

```ShellSession
$ _hostname="julia"
$ hostnamectl set-hostname ${_hostname}
```

Set the locale:

Edit `/etc/locale.conf` and uncomment just the line containing your locale (e.g. for me is `LANG="en_US.utf8"`) and be sure the other lines are commented too.

$ localectl set-locale LANG=<LOCALE>
To change the virtual console keymap:

Set the virtual console keymap:

```ShellSession
$ localectl set-keymap <KEYMAP>
```

Set the X11 layout:

```ShellSession
localectl set-x11-keymap <LAYOUT>
```

Set time and date:

```ShellSession
$ timedatectl TODO
```
