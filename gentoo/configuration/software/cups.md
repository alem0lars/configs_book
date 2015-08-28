# CUPS

```ShellSession
# emerge "net-print/cups"
```

Any user that needs to print should be added to the `lp` group:

```ShellSession
# gpasswd -a ${username} lp
```

In order to be able to add printers and edit them via CUPS's web interface,
any system user that is allowed to edit these settings should be in the
`lpadmin` group:

```ShellSession
# gpasswd -a ${username} lpadmin
```

## Install printers

In general, install the specific printer PPD file (from
[here](http://www.openprinting.org/drivers)).

In case you need to use HP printers, run:

```ShellSession
# emerge "net-print/hplip"
```
