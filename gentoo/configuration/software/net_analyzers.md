# Network Analyzers

## TCP packet demultiplexers

```ShellSession
# emerge "net-analyzer/tcpflow"
# emerge "net-analyzer/tcpdump"
```

## Wireshark

```ShellSession
# emerge "net-analyzer/wireshark"
```

### Configuration

To be able to use `Wireshark` with a normal user, you need to add it to
the `wireshark` group:

```ShellSession
# _username="alem0lars" # Replace with yours.
# gpasswd -a ${_username} wireshark
```

## mtr

```ShellSession
# emerge "net-analyzer/mtr"
```

## p0f

```ShellSession
# emerge "net-analyzer/p0f"
```

## Tsung

```ShellSession
# emerge "net-analyzer/tsung"
```

## NMap

```ShellSession
# emerge "net-analyzers/nmap"
```

## Test network speed

```ShellSession
# emerge "net-analyzer/speedtest-cli"
```
