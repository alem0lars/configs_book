## Setup
### Initial

* Configure static network address (with `nmcli`)
* Set hostname (*both qualified with domain and unqualified*) in:
  * `/etc/sysconfig/network`
  * `/etc/hosts`
* Set missing or bad locales in `/etc/locale.conf` (to check them use the command `locale`)

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
