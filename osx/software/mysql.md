# MySQL

## Installation

```ShellSession
$ brew install mysql --with-archive-storage-engine --with-blackhole-storage-engine
```

## Configuration

* To have launchd start mysql at login:
  
  ```ShellSession
  $ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
  ```
