# MySQL

## Installation

```ShellSession
$ brew install mysql --enable-local-infile --enable-memcached --with-archive-storage-engine --with-blackhole-storage-engine
```

## Configuration

* To have launchd start mysql at login:
  
  ```ShellSession
  $ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
  ```
