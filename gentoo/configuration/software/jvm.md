# JVM

## Java

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

## Scala

```ShellSession
# emerge "dev-lang/scala"
```

### Select a `Scala` version

Set the default scala version:

```ShellSession
# eselect scala set 1 # Replace 1 with your chosen Scala profile.
```

## Tomcat

```ShellSession
# emerge "www-servers/tomcat"
```

Now you need to manually install `tomcat-dbcp.jar` because it's not installed by
default (see [Issue #144276](https://bugs.gentoo.org/show_bug.cgi?id=144276)):

* Download and extract the tomcat archive from [here](http://tomcat.apache.org).
* Now from inside the extracted folder run:

  ```ShellSession
  # _version=8 # The installed tomcat package version number (e.g. `7` or `8`).
  # cp ./lib/tomcat-dbcp.jar /usr/share/tomcat-${_version}/lib
  ```

### Configuration

To access the manager app, you should setup users to something like:

```XML
<role rolename="manager-gui" />
<role rolename="manager-script" />
<role rolename="manager-jmx" />
<user username="main-manager" password="<password>" roles="manager-gui,manager-script,manager-jmx" />
```

## Additional resources

### Ant

```ShellSession
# emerge "dev-java/ant"
# emerge "dev-java/ant-ivy"
```

### Maven

```ShellSession
# emerge "dev-java/maven-bin"
```

### SBT

```ShellSession
# emerge "dev-java/sbt"
```

### Linters / Checkers

```ShellSession
$ emerge findbugs
$ emerge checkstyle
```
