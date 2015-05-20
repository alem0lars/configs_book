# `Java`

## Installation

```ShellSession
$ emerge virtual/jdk virtual/jre
```

## Set the default virtual machine

To set the `Java` `nsplugin` run:

```ShellSession
$ eselect java-nsplugin set ${_n} # Replace `${_n}` with your chosen `Java` `nsplugin`.
```

Set the default `Java` virtual machine system-wide:

```ShellSession
$ eselect java-vm set system ${_n} # Replace `${_n}` with your chosen user-wide `Java` virtual machine.
```

For every user (except `root`) set the default `Java` virtual machine user-wide:

```ShellSession
$ eselect java-vm set user ${_n} # Replace `${_n}` with your chosen user-wide `Java` virtual machine.
```
