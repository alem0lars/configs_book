## Setup

### Network

* Configure static network address (with `nmcli`)
* Set hostname (*both qualified with domain and unqualified*) in:
  * `/etc/sysconfig/network`
  * `/etc/hosts`

### Locale

* Set missing or bad locales in `/etc/locale.conf` (to check them use the command `locale`)

### Decrypt partitions via SSH

With this step, you can enter the encryption passphrase with an early SSH login, allowing to perform full headless login.

Both [dropbear](https://matt.ucc.asn.au/dropbear/dropbear.html) and [busybox](http://www.busybox.net/about.html) are required.

Busybox is already available in CentOS, but you need to install dropbear: `yum install dropbear`.

TODO

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
