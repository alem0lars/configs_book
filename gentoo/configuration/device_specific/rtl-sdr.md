# RTL SDR

If you want to support a Realtek device as software defined radio, run:

```ShellSession
# emerge "net-wireless/rtl-sdr"
```

## GNURadio support

To have Realtek blocks in GNURadio, you need to have the following use-flags
enabled:

- `rtlsdr`

Then, run:

```ShellSession
# emerge "net-wireless/gr-osmosdr"
```

## Allow capturing

Only users in the USB group can capture. To allow your user to capture, run:

```ShellSession
# _username="alem0lars" # Replace with your username.
# gpasswd -a ${_username} usb
```
