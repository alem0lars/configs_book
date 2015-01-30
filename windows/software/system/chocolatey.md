# Chocolatey

## Installation

Run the following commands in an administrator console:

```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

# ChocolateyGUI

This is the GUI for Chocolatey.

## Installation

Run the following commands in an administrator console:

```
choco install ChocolateyGUI
```
