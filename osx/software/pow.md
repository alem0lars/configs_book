# Pow

## Installation

```ShellSession
$ brew install pow
```

## Configuration

* Create the required host directories:

  ```ShellSession
  $ mkdir -p ~/Library/Application\ Support/Pow/Hosts
  $ ln -s ~/Library/Application\ Support/Pow/Hosts ~/.pow
  ```

* Setup port 80 forwarding and launchd agents:

  ```ShellSession
  $ sudo pow --install-system
  $ pow --install-local
  ```

* Load launchd agents:

  ```ShellSession
  $ sudo launchctl load -w /Library/LaunchDaemons/cx.pow.firewall.plist
  ```

## Powder

### Installation

```ShellSession
$ sudo gem install powder
```
