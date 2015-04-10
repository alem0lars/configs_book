# Host setup

## Installation

You need to install an operating system in the physical host.
My distro of choice for server installations is CentOS.

*This guide isn't for complete noobs, I'm not going to explain you how to install a distro, if you aren't able to, omg you shouldn't have permissions to manage a server or a cluster!*

I will just highlight things I consider important.

### Partitioning

You should use LVM for partitioning.

Create the following volume groups:
* `centos`

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
* An EFI partition..

### Users

* Create a user called `admin`, as an administrator. You'll use it instead of using directly `root`.
* Set the password for the user `root` (ofc different than the password used for `admin`).

## Setup

### Network

### Setup hostname

* `/etc/hostname`.
* `/etc/sysconfig/network`: (`HOSTNAME="fqdn"`).
* `/etc/hosts`: prepend in both lines the fqdn and name.

#### Setup bridge connection

```ShellSession
$ nmcli c add type bridge autoconnect yes con-name br0 ifname br0 # Add bridge `br0`.
```

Edit the connection, set the properties: `ipv4.addresses`, `ipv4.method`, `ipv4.dns` and persistently save (`save persistent`).

Remove previously existing connections with the interface of interest (for me was a connection called `eno1` to the interface `eno1`).

Add an interface again as a member of `br0`:

```ShellSession
$ _ifname="eno1"
$ nmcli c add type bridge-slave autoconnect yes con-name ${_ifname} ifname ${_ifname} master br0 
```

Restart NetworkManager:

```ShellSession
$ systemctl restart NetworkManager
```

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

### Install KVM

```
$ yum install qemu-kvm libvirt virt-install bridge-utils
```

Enable the libvirtd daemon:

```ShellSession
$ systemctl start libvirtd
$ systemctl enable libvirtd 
```

Now typing `ip addr` you should see the interfaces `virbr0`, `virtbr0-nic`, `br0`, `eno1` up and running.

### Install GlusterFS

```ShellSession
$ yum install glusterfs-server nfs-utils vdsm-gluster system-storage-manager
```

Reboot the system.

Configure the filesystem:

```ShellSession
$ _pool="gluster" # The name of the gluster pool to be used.
$ _dev="/dev/sda1" # The device to add to gluster.
$ _fstype="ext4"
$ _name="gluster"

$ ssm add -p ${_pool} ${_dev}
$ ssm create -p ${_pool} --fstype ${_fstype} -n ${_name}
```

Next, modify your `/etc/fstab` to add the new partition:

```ShellSession
$ mkdir /gluster
```

Edit `/etc/fstab` and add the following line:

```
UUID=<gluster_dev_uuid> /gluster ext4 defaults 0 0
```

substituiting the UUID returned by `blkid /dev/gluster/gluster` to `<gluster_dev_uuid>`.

Mount your new partition:

```ShellSession
$ mount -a
```

Next, we'll create some mount points for our Gluster volumes-to-be. We'll have separate Gluster volumes for our oVirt engine and for our data domain:

```ShellSession
$ mkdir -p /gluster/{engine,data}/brick
```

Enable the GlusterFS daemon:

```ShellSession
$ systemctl stop glusterd
$ systemctl start glusterd
$ systemctl enable glusterd 
```

### Install oVirt

* Install oVirt: `yum install ovirt-engine`.
* Setup the engine: `engine-setup`.
