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

1. Create LVM based partitioning layout (*suggested*).
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
  * If you don't have an `UEFI` system this partition is *optional*: you can have
    the `/boot` directory inside the `root` partition instead of having a
    separate partition. However, *creating a separate partition is always
    preferred*.

4. `efi` partition:
  * *Needed if you have a `UEFI` system*.
  * Holds informations used by the boot-manager and boot-loaders.
  * If you're doing a dualboot setup with `OSX` you already have this partition.

5. `tmp` partition:
  * It will be mounted in `/tmp`.
  * This partition is *optional*: other options include having the `/tmp` directory inside the
    `root` partition or mounting `tmp` in `RAM`. In that cases you shouldn't have this
    partition. If you have enough RAM for `/tmp` (it depends, but typically `8GB` is
    enough), the RAM method is preferred.

Of course you can add as many partitions as you want but keep in mind you should
create a new partition only if you have a really valid reason to do that,
because many partitions have it's drawbacks (resizing partitions is a delicate
task).

#### Additional resources

If doing a `GNU/Linux`-`OSX` dualboot setup, then read its dedicate
[partitioning suggestions](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#partitioning-suggestions).

### Create EFI partition (*UEFI-only*)

*This step is needed only if you're using `UEFI`.*

See [here](./uefi-create.md)

### Create other partitions

#### Encryption

*Optional.*

See [here](./encryption.md)

#### With `LVM`

See [here](./format-lvm.md)

#### Without `LVM`

See [here](./format-plain.md)

### Mount the partitions

```ShellSession
# swapon "/dev/sda4" # Replace with your swap partition.
# mkdir "/mnt/gentoo"
# mount "/dev/sda5" "/mnt/gentoo" # Replace with your root partition.
```

Of course for any additional partition you have you should create the directory
(relative to the root path) and mount the partition into it.

For example if you have a `var` partition in `/dev/sda7`, you should do:

```ShellSession
# mkdir "/mnt/var"
# mount "/dev/sda7" "/mnt/gentoo/var"
```

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
# mkdir /etc/portage/repos.conf
# cp /usr/share/portage/config/repos.conf /etc/portage/repos.conf/gentoo.conf
# emerge --sync
```

## Set the right profile

```
# eselect profile list # Will list all of the available profiles.
# eselect profile set <X> # Will set the profile to <X>
```

My personal preference is the *`systemd`*, *multilib*, *non-hardened* profile.

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
# mount "/dev/sda1" "/boot"
```

Now you can create the directory for storing gentoo boot images and related
files:

```ShellSession
# mkdir -p /boot/EFI/gentoo
```

## Bootloader

There are many bootloaders available:
* `rEFInd`: useful if you have dual-boot with MacOSX.
* `systemd-boot`: minimalistic, best approach for `EFI`-based systems using `systemd`.
* `GRUB2`: bootloader with a ton of features. I suggest you to use this choice if you don't have an `EFI` system.

### Initial notes

In a `EFI` system, you need to be sure the `efivarfs` is mounted.
If `efivarfs` is not automatically mounted at `/sys/firmware/efi/efivars` by `systemd` during boot, then you need to manually mount it to expose UEFI Variable support to the userspace tools like `efibootmgr`, etc.:

```ShellSession
# mount -t efivarfs efivarfs /sys/firmware/efi/efivars
```

Also I suggest you to install common tools:

```ShellSession
# emerge "sys-boot/efibootmgr"
# emerge "sys-libs/efivar"
```

### systemd-boot

Consider the `EFI` partition mounted in `$esp`.

Install the bootloader:

```ShellSession
# bootctl --path=/boot install
```

### rEFInd

The bootloader of choice is `rEFInd`.

To install it follow the [official installation guide](http://www.rodsbooks.com/refind/installing.html).

#### Notes

You may already have the bootloader installed (e.g. if using a dualboot setup).
In that case, *skip this step* (e.g. if another OS is already installed
(i.e. bootloader was installed in that installation) or if you've done a
[dualboot setup](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#step-3-install-the-boot-manager-refind)).

## Install the kernel

```ShellSession
# emerge "app-admin/mcelog"
# emerge "sys-kernel/gentoo-sources"
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
# cp "/usr/src/linux/arch/x86_64/bzImage" "/boot/EFI/gentoo/kernel-latest.efi"
```

#### Additional resources

If doing a `GNU/Linux`-`OSX` dualboot setup, then read its dedicate
[kernel configuration](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#kernel-configuration).

## Generate `initramfs`

Sometimes generating an `initramfs` is mandatory, sometimes not.
However, *it's always suggested*!

Install `dracut`:

```ShellSession
# echo "sys-kernel/dracut" >> "/etc/portage/package.keywords/tmp"
# emerge sys-kernel/dracut
```

Generate the image `initramfs`:

```
# dracut
# mv "$(ls /boot/initramfs*)" "/boot/EFI/gentoo/initramfs-latest.img"
```

## Configure the bootloader

### systemd-boot

Add the `gentoo` entry under edit `/boot/loader/entries/gentoo.conf`:

```
TODO
```

Edit `/boot/loader/loader.conf` to set the `gentoo` entry as the default one:

```
timeout 4
default arch
```

### rEFInd

Edit the file `refind.conf` and add the menuentry:

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

```ShellSession
# echo > /etc/fstab
```

Add your `swap` partition:

```ShellSession
# echo "/dev/sda4 none swap sw 0 0" >> /etc/fstab # Replace it with your swap device.
```

Add your `root` partition:

```ShellSession
# echo "/dev/sda5 / ext4 noatime 0 1" >> /etc/fstab # Replace it with your root device.
```

Add directories holding temporary files in `RAM`:

```ShellSession
tmpfs		/var/tmp/portage		tmpfs	size=2G,uid=portage,gid=portage,mode=775,noatime	0 0
# echo "tmpfs /tmp tmpfs defaults,noatime,nosuid,size=6G 0 0" >> /etc/fstab # Replace your desired size.
# echo "tmpfs /var/tmp/portage tmpfs uid=portage,gid=portage,mode=775,noatime,size=4G 0 0" >> /etc/fstab # Replace with your desired size.
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
