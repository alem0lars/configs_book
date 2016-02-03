# Wacom

If you need to support a Wacom tablet you need the X11 driver:
`xf86-input-wacom`. To enable it add `wacom` to `INPUT_DEVICES` and run:

```ShellSession
# emerge x11-base/xorg-drivers
```

Also, you need to enable the following kernel options:

- `Wacom Intuos/Graphire tablet support (USB)`
