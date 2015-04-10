# Host setup

## Installation

You need to install an operating system in the physical host.
My distro of choice for server installations is CentOS.

*This guide isn't for complete noobs, I'm not going to explain you how to install a distro, if you aren't able to, omg you shouldn't have permissions to manage a server or a cluster!*

I will just highlight things I consider important.

### Partitioning

You should use LVM for partitioning.

Create the following volume groups:
* `vg_host`: Contains the logical volumes related to the host itself.
* `vg_gluster`: Contains logical volumes that contribute to GlusterFS.

Create the following logical volumes:
* `swap`:
  * Size: `8GB`
  * Volume group: `host`
* `root`:
  * Size: `60GB` (approx)
  * Volume group: `host`
* `gluster0`:
  * Size: remaining disk space (`<hdd_size> - <root_size> - <swap_size>`)
  * Volume group: `gluster`

Also, you should create a boot partition *outside LVM*:
* `boot`:
  * Size: `500MB`
  * Filesystem: `ext4`
  * Mountpoint: `/boot`

### Users

* Create a user called `admin`, as an administrator. You'll use it instead of using directly `root`.
* Set the password for the user `root` (ofc different than the password used for `admin`).

## Setup

### Network

* Configure static network address (with `nmcli`)
* Set hostname (*both qualified with domain and unqualified*) in:
  * `/etc/sysconfig/network`: (`HOSTNAME="fqdn"`).
  * `/etc/hosts`: add in both lines the name and fqdn.

### Locale

* Set missing or bad locales in `/etc/locale.conf` (to check them use the command `locale`)

### Decrypt partitions via SSH

With this step, you can enter the encryption passphrase with an early SSH login, allowing to perform full headless login.

Both [dropbear](https://matt.ucc.asn.au/dropbear/dropbear.html) and [busybox](http://www.busybox.net/about.html) are required.

Busybox is already available in CentOS, but you need to install dropbear: `yum install dropbear`.

TODO: https://github.com/mdcurtis/dracut-earlyssh http://unix.stackexchange.com/questions/5017/ssh-to-decrypt-encrypted-lvm-during-headless-server-boot

### Repositories

* Add EPEL repository: `yum install epel-release`
* Add oVirt repository: `yum localinstall -y http://resources.ovirt.org/pub/yum-repo/ovirt-release35.rpm`

After adding all repositories run: `yum update`

### Install basic tools

* VIm: `yum install vim`
* TMux: `yum install tmux`

### Install GlusterFS, oVirt

* Install oVirt: `yum install ovirt-hosted-engine-setup`
* Install GlusterFS: `yum install glusterfs-server nfs-utils vdsm-gluster system-storage-manager`

TODO
