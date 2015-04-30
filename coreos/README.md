# CoreOS Setup Tutorial

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

## Troubleshooting

### GPT:Alternate GPT header not at the end of the disk

After installation if you get the message: `GPT:Alternate GPT header not at the end of the disk.` you should fix that issue by running `parted`:

```ShellSession
$ _device="/dev/sda" # Set to your device path.
$ sudo parted "${_device}"
```

Then execute the command: `print`. You will be prompted with `Fix/Ignore/Cancel` questions and respond `Fix` to all of those questions. After that, execute the command `quit` to exit from parted.

Now your system is ready for the first boot. Execute:

```ShellSession
$ sudo systemctl reboot
```

to reboot your system.

## Login

To login you should use SSH with the user that owns the private-key matching the deployed public-key as the `core` user:

```ShellSession
$ _host_ip="10.0.10.1" # Set to your CoreOS host IP address (the same as configured in `cloud-config.yaml`).
$ ssh core@${_host_ip}
```

Boom! You'd be in!
