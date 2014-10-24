# Redis

## Installation

```ShellSession
$ brew install redis
```

## Configuration

* To have launchd start redis at login:
  ```ShellSession
  $ ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
  ```
