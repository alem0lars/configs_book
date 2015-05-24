# Network Analyzers

## `TCP`*

### Installation

```ShellSession
# emerge "net-analyzer/tcpflow"
# emerge "net-analyzer/tcpdump"
```

## `Wireshark`

### Installation

```ShellSession
# emerge "net-analyzer/wireshark"
```

### Configuration

To be able to use `Wireshark` with a normal user, you need to add it to the `wireshark` group:

```ShellSession
# _username="alem0lars" # Replace with yours.
# gpasswd -a ${_username} wireshark
```

## `mtr`

### Installation

```ShellSession
# emerge "net-analyzer/mtr"
```

## `p0f`

### Installation

```ShellSession
# emerge "net-analyzer/p0f"
```
