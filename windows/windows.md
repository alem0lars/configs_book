# Windows

## Install

## Setup

See [Setup Instructions](./setup.md)

## Software

### Chocolatey

#### Installation

Run the following commands in an administrator console:

```
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

### ChocolateyGUI

#### Installation

Run the following commands in an administrator console:

```
choco install ChocolateyGUI
```

### ConEmu

#### Installation

Run the following commands in an administrator console:

```
choco install conemu
choco install jayhankins.conemuconfig
```

#### Configuration

* Enable `Enable Single instance mode`.
* Enable `Enable automatic updates`.

### 7Zip

#### Installation

Run the following commands in an administrator console:

```
choco install 7zip
choco install 7zip.commandline
```

### Avira Free Antivirus

#### Prerequisites

Turn off Windows Defender.

#### Installation

Run the following commands in an administrator console:

```
choco install avirafreeantivirus
```

### Unity3d

#### Installation

Run the following commands in an administrator console:

```
choco install unity
choco install unitywebplayer
```

### Visual Studio

#### Installation

Run the installer.

#### Extensions

* *ReSharper* (choose all products in the installer), with the following ReSharper extensions:
  * *Jetbrains.NuPeek*
* *Visual Studio 2013 Tools for Unity*
* *VsVim*

### NuGet tools

Run the following commands in an administrator console:

```
choco install nuget.commandline
```
