# Wacom

If you need to support a Wacom tablet you need the X11 driver: `xf86-input-wacom`

```ShellSession
# emerge "x11-drivers/xf86-input-wacom"
```

Also, you need to enable the following kernel options:

- `Wacom Intuos/Graphire tablet support (USB)`
