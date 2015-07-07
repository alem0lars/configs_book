# `JVM`

## Java

### Installation

```ShellSession
# emerge "virtual/jdk"
# emerge "virtual/jre"
# emerge "dev-java/javatoolkit
```

### Set the default virtual machine

To set the `Java` `nsplugin` run:

```ShellSession
$ eselect java-nsplugin set ${_n} # Replace `${_n}` with your chosen `nsplugin`.
```

Set the default `Java` virtual machine system-wide:

```ShellSession
$ eselect java-vm set system ${_n} # Replace `${_n}` with your chosen user-wide `Java` virtual machine.
```

For every user (except `root`) set the default `Java` virtual machine user-wide:

```ShellSession
$ eselect java-vm set user ${_n} # Replace `${_n}` with your chosen user-wide `Java` virtual machine.
```

## `Scala`

### Installation

```ShellSession
# emerge "dev-lang/scala"
```

### Select a `Scala` version

Set the default scala version:

```ShellSession
# eselect scala set 1 # Replace 1 with your chosen Scala profile.
```

## Additional resources

### `Ant`

#### Installation

```ShellSession
# emerge "dev-java/ant"
# emerge "dev-java/ant-ivy"
```

### `Maven`

#### Installation

```ShellSession
# emerge "dev-java/maven-bin"
```

### `SBT`

#### Installation

```ShellSession
# emerge "dev-java/sbt"
```

### Linters / Checkers

#### Installation

```ShellSession
$ emerge findbugs
$ emerge checkstyle
```
