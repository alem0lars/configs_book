# MongoDB

## Installation

```ShellSession
$ brew install mongodb --with-openssl
```

## Configuration

* To have launchd start mongodb at login:
  
  ```ShellSession
  $ ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents
  ```

## Development tools

### MongoHUB

```ShellSession
$ brew cask install mongohub
```
