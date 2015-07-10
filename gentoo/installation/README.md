# `Gentoo` Installation

This tutorial let you install a functioning but not configured `Gentoo` system.

This is because IMHO 

## Requirements

You'll need Internet connectivity.

## Boot installer

Boot the installer, which is any live `GNU/Linux`.

Check if you can reach Internet (e.g. `ping 8.8.8.8`) and if your `DNS` setup is
correct (e.g. `ping www.google.com`).

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
  * If you haven't an `UEFI` system this partition is *optional*: you can have
    the `/boot` directory inside the `root` partition instead of having a
    separate partition. However, creating a separate partition is always
    preferred.

4. `efi` partition:
  * Holds informations used by the boot-manager and boot-loaders.
  * If you're doing a dualboot setup with `OSX` you already have this partition.

5. `tmp` partition:
  * It will be mounted in `/`.
  * This partition is *optional*: you can have the `/tmp` directory inside the
    `root` partition or mounted in `RAM`. In that cases you shouldn't have this
    partition. If you have enough RAM for `/tmp` (it depends, but IMHO `8GB` is
    enough), then the `RAM` method is preferred.

Of course you can add as many partitions as you want but keep in mind you should
create a new partition only if you have a really valid reason to do that,
because many partitions have it's drawbacks (resizing partitions is a delicate
task).

#### Additional resources

If doing a `GNU/Linux`-`OSX` dualboot setup, then read its dedicate
[partitioning suggestions](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#partitioning-suggestions).

### Create partitions

#### With `LVM`

TODO

#### Without `LVM`

Open `parted` (the partitioning tool of choice):

```ShellSession
# _dev_name="/dev/sda" # Replace with the path of your disk device.
# parted -a optimal "${_dev_name}"
# unit mib # Set MiB as the default unit (the unit to use when no one is specified).
```

For each partition you want to create, do the following:

```
(parted) mkpart primary <FILESYSTEM> <START> <END>
```

where:

* `<FILESYSTEM>`: replace with the filesystem you want to use for that partition
  (e.g. `ext4`, `linux-swap`, etc..).
* `<START>`: the first byte to use. It's the `End` of the previous partition
  (you can see it with the command `print`) *plus `1MiB`* which is `1` because
  the current default unit is `MiB`, for aligning the partitions correctly.
* `<END>`: the last byte to use. You can calculate it as `<START> + <SIZE>`
  where `<SIZE>` is the size you want to give at the partition.

Assign a name to the created partition:

```
(parted) name <NUMBER> <NAME>
```

where:

* `<NUMBER>`: is the partition number. It identifies which partition you want to
  give the name to.
* `<NAME>`: the name to assign to the created partition.

### Assign labels to partitions

Every partition you've created should have a label associated. Doing this,
allows you to find partitions by their label (under `/dev/disk/by-label`).

To do so, see [here](https://wiki.archlinux.org/index.php/Persistent_block_device_naming#by-label)

### Format the partitions

Every partition you've created should be formatted. The command depends on the
filesystem:

* `ext4`:

  ```ShellSession
  # _dev_path="/dev/sda5" # Replace with your path.
  # mkfs.ext4 "${_dev_path}"
  ```

* `swap`:

  ```ShellSession
  # _dev_path="/dev/sda4" # Replace with your path.
  # mkswap "${_dev_path}"
  ```

### Mount the partitions

```ShellSession
# _swap_dev_path="/dev/sda4" # Replace with your swap path.
# _root_dev_path="/dev/sda5" # Replace with your root path.
# swapon "${_swap_dev_path}"
# mkdir "/mnt/gentoo"
# mount "${_root_dev_path}" "/mnt/gentoo"
```

Of course for any additional partition you have you should create the directory
(relative to the root path) and mount the partition into it. For example if you
have a `var` partition in `/dev/sda7`, then you've done:
`mkdir /mnt/var  && mount /dev/sda7 /mnt/gentoo/var`.

## Check the date is correct

([Stolen from gentoo handbook](https://wiki.gentoo.org/wiki/Handbook:AMD64/Full/Installation), ty :D)

Before installing Gentoo, make sure that the date and time are set correctly.
A mis-configured clock may lead to strange results in the future!

To verify the current date/time, run date:

```ShellSession
$ date
Fri Mar 29 16:21:18 UTC 2005
```

If the date/time displayed is wrong, update it using the date `MMDDhhmmYYYY`
syntax (Month, Day, hour, minute and Year). At this stage, it is recommended to
use `UTC` time. Later on during the installation, the timezone will be defined.

For instance, to set the date to `March 29th, 16:21` in the year `2014`:

```ShellSession
$ date 032916212014
```

## Download installation files

Download the `stage3` from [http://www.gentoo.org/main/en/mirrors.xml](http://www.gentoo.org/main/en/mirrors.xml)
(it's located inside the directory `releases/amd64/autobuilds`).

and save them to the installation root mount directory (e.g. `/mnt/gentoo`).

## Install `stage3`

Go to the installation root mount directory and extract the downloaded `stage3`
archive:

```ShellSession
$ _root_dir="/mnt/gentoo"
$ cd "${_root_dir}"
$ tar xvjpf "stage3-*.tar.bz2"
$ rm "stage3-*.tar.bz2"
```

## Before `chroot`

### Set options

Before installing other packages you should (temporarly) set some
configurations. Later we will set them better but now we just need to be able to
install `Gentoo`, nothing more.

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

To make sure that the new environment works properly, certain filesystems need
to be made available there as well:

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

When using non-`Gentoo` installation media, this might not be sufficient. Some
distributions make `/dev/shm` a symbolic link to `/run/shm/` which, after the
`chroot`, becomes invalid.
Making `/dev/shm/` a proper `tmpfs` mount up front can fix this:

```ShellSession
# rm /dev/shm && mkdir /dev/shm
# mount -t tmpfs -o nosuid,nodev,noexec shm /dev/shm
```

Also ensure that mode `1777` is set:

```ShellSession
# chmod 1777 /dev/shm
```

## Install `portage`

```ShellSession
# emerge-webrsync
# mkdir /etc/portage/repos.conf/gentoo.conf
# cp /usr/share/portage/config/repos.conf /etc/portage/repos.conf/gentoo.conf
# emerge --sync
```

## Set the right profile

I suggest you to use the `hardened` profile. It should appear as something like
`[14] hardened/linux/amd64/`.

```
# eselect profile list # Will list all of the available profiles.
# eselect profile set <X> # Will set the profile to <X>
```

## Install `systemd`

* Add `systemd` to your useflags.
* Run emerge, so packages relying upon systemd will be aware of the useflag:

  ```ShellSession
  # emerge -avDN @world
  ```

### Notes

If you get dependency problems (`sys-fs/udev` is blocking `sys-apps/systemd`),
`sys-fs/udev` may be in the world file and it shouldn't be there because it's
included inside `systemd`.

Try to resolve this by:

```ShellSession
# emerge --deselect sys-fs/udev
```

## Set `gcc`

After the upgrade you've just done, you'll have available hardened `gcc`.

The following command shows you the available `gcc` profiles:

```ShellSession
# gcc-config -l
```

Enable the profile like `[1] x86_64-pc-linux-gnu-4.8.4`.

In this example the profile is number 1, so to enable it we'll do:

```Shell
# _profile_number=1
# gcc-config ${_profile_number}
```

## Reload the environment

```ShellSession
# env-update
# source /etc/profile
```

## Mount the `EFI` partition into `/boot`

```ShellSession
# _efi_device_path="/dev/sda1"
# mount "${_efi_device_path}" "/boot"
```

Now you can create the directory for storing gentoo boot images and related
files:

```ShellSession
# mkdir -p /boot/EFI/gentoo
```

## Install the bootloader

The bootloader of choice is `rEFInd`.

To install it follow the [official installation guide](http://www.rodsbooks.com/refind/installing.html).

### Notes

You may already have the bootloader installed (e.g. if using a dualboot setup).
In that case, *skip this step* (e.g. if another OS is already installed
(i.e. bootloader was installed in that installation) or if you've done a
[dualboot setup](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#step-3-install-the-boot-manager-refind)).

## Install the kernel

```ShellSession
# emerge mcelog hardened-sources
```

## Configure the kernel

At this moment, we just need to be able to boot the kernel. Don't try to do a
complete and the best configuration right now.
You'll do it later (with a running system you'll feel more comfortable) or
maybe you've saved it somewhere (like me, I use `Fizzy` to manage my kernel
configuration as well as other configs) and you'll restore it, so this work
will be useless after the restore.

```ShellSession
# cd "/usr/src/linux"
# make menuconfig
```

Then enable the following options:

* [Generic options](https://wiki.gentoo.org/wiki/Handbook:AMD64/Installation/Kernel)
* Those for [`systemd` support](https://wiki.gentoo.org/wiki/Systemd).
* The ones needed for your physical hardware (see below).

Finally, compile the kernel:

```ShellSession
# cd "/usr/src/linux"
# make
# make modules_install
# cp "/usr/src/linux/arch/x86_64/bzImage" "/boot/EFI/gentoo/kernel-hardened-latest.efi"
```

#### Additional resources

If doing a `GNU/Linux`-`OSX` dualboot setup, then read its dedicate
[kernel configuration](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#kernel-configuration).

## Generate `initramfs`

Sometimes generating an `initramfs` is mandatory, sometimes not.
However, *it's always suggested*!

Install `dracut`:

```ShellSession
# echo "sys-kernel/dracut" >> "/etc/portage/package.keywords"
# emerge sys-kernel/dracut
```

Generate the image `initramfs`:

```
# dracut
# mv "$(ls /boot/initramfs*)" "/boot/EFI/gentoo/initramfs-latest"
```

## Configure the bootloader

Add the following menu entry in `/boot/EFI/gentoo/refind/refind.conf`:

```
menuentry Gentoo {
  volume KERNELS
  loader /EFI/gentoo/kernel-hardened-latest.efi
  initrd /EFI/gentoo/initramfs-latest
}
```

## Configure `fstab`

Edit the file `/etc/fstab` and one entry (line) for each partition you want to
automatically mount at boot.

First of all, cleanup the file.

```
# echo > /etc/fstab
```

Add your `swap` partition:

```ShellSession
# _swap_dev_path="/dev/sda4" # Replace it with your swap device.
# echo "${_swap_dev_path} none swap sw 0 0" >> /etc/fstab
```

Add your `root` partition:

```ShellSession
# _root_dev_path="/dev/sda5" # Replace it with your root device.
# _root_def_fs="ext4
# echo "${_root_dev_path} / ${_root_dev_fs} noatime 0 1" >> /etc/fstab
```

Add directories holding temporary files in `RAM`:

```ShellSession
# _tmp_size="6G"
# _tmp_portage_size="8G"
# echo "tmpfs /tmp tmpfs defaults,noatime,nosuid,size=${_tmp_size}" >> /etc/fstab
# echo "tmpfs /var/tmp/portage tmpfs defaults,noatime,nosuid,size=${_tmp_portage_size}" >> /etc/fstab
```

### Notes

The example above mounts `tmp` in `RAM`. Ignore that line if you don't want that
and, if you have a separate partition, add an entry for it.

Be sure to add additional entries for all additional partitions you have and are
not listed in the example above.

## Set root password

```ShellSession
# passwd
```

## Reboot

yay! Now the basic installation is finished. *You can reboot your system but
keep in mind that nothing is configured yet*.

```ShellSession
# exit
# umount -a
# reboot
```
