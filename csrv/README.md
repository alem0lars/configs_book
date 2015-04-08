# CSRV

A container-based cluster installation, using CoreOS.

## Create configuration

You need to create a configuration file containing the informations used to install CoreOS.

This is an example based on mine: [cloud-config.yaml](./assets/host-cloud-config.yaml).
Note that you should customize it according to your host / cluster parameters.

## Installation

```ShellSession
$ _device="/dev/sda" # Set to your device path.
$ _channel="stable" # Set to "stable" or "beta". I usually prefer stable since it's what used normally in production.
$ _config="/home/core/cloud-config.yaml" # The path to the configuration file (see above).
$ sudo coreos-install -d "${_device}" -C "${_channel}" -c "${_config}"
```
