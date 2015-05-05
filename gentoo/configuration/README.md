# `Gentoo` Configuration

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
