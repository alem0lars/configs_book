# Network Analyzers

## Installation

```ShellSession
$ emerge wireshark
$ emerge tcpflow
$ emerge tcpdump
```

## Configuration

To be able to use `Wireshark` with a normal user, you need to add it to the `wireshark` group:

```ShellSession
$ _username="alem0lars" # Replace with yours.
$ gpasswd -a ${_username} wireshark
```
