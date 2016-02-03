# Temporary configuration

This is because we need a basic working system before configuring it perfectly.

## Configure the network

The network daemon of choice is `systemd-networkd`.

For configuring the daemon you have 2 approaches available:

1. Perfectly configure the connections available in the system. You want to use this approach if you don't have the right configurations already managed with a configuration management system or stored somewhere (like a `git` repository).
2. Configure the connections just to be able to connect to the Internet. *I recommend and use this approach* because I want to manage all of my configurations (with `Fizzy`) and they're already stored [somewhere](https://github.com/alem0lars/configs). In this case, if you have a cable connection with `dhcp`, the following networking configuration should be enough:

  Edit `/etc/systemd/network/wired.network`:

  ```
  [Match]
  Name=enp*

  [Network]
  DHCP=yes
  ```

In any case, you can find more informations [here](https://wiki.archlinux.org/index.php/Systemd-networkd#Basic_usage).

## Set some basic system-wide informations

Set the hostname:

```ShellSession
$ _hostname="julia"
$ hostnamectl set-hostname ${_hostname}
```

Set the locale:

```
$ _locale="en_US.utf8"
$ localectl set-locale LANG=${_locale}
```

Set the virtual console keymap:

```ShellSession
$ _keymap="us"
$ localectl set-keymap ${_keymap}
```

Set time and date:

```ShellSession
$ _timezone="UTC"
$ timedatectl set-timezone ${_timezone}
$ timedatectl set-ntp true
```
