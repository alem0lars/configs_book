# Windows

## Install

## Setup

### Taskbar and Navigation properties

* Enable  `Taskbar` → `Use small taskbar buttons`.
* Enable  `Navigation` → `When I sign in ...`.
* Enable  `Navigation` → `Show my desktop ...`.
* Disable `Navigation` → `Show Start on the display ...`.
* Enable  `Navigation` → `Show the Apps view automatically when I go to Start`.
* Enable  `Navigation` → `Search everywhere instead ...`.
* Enable  `Navigation` → `List desktop apps first ...`.

### Folder options

* Disable `View` → `Hide empty drives`.
* Disable `View` → `Hide extensions for known file types`.
* Disable `View` → `Hide folder merge conflicts`.
* Disable `View` → `Hide protected operating system files`.
* Disable `View` → `Use Sharing Wizard`.

### Disable hot corners

Open PC Settings, then:

* Disable both options present in `PC and devices` → `Corners & edges` → `Corner navigation` section.
* Disable `PC and devices` → `Corners and edges` → `When I swipe in from ...`.

### Disable Bing search integration

Open PC Settings, then:

* Disable `Search and apps` → `Get search suggestions and web results ...`.

### Disable Windows Store

Open `gpedit.msc`, go to: `Computer Configuration` → `Administartive Templates` → `Windows Components` → `Store` and:

* Enable `Turn off the Store application`.

### Change pointer

Open PC Settings, then:

* Choose the second option (only black) in `Ease of Access` → `Mouse` → `Pointer color`.

### Change visual options

Open PC Settings, then:

* Disable `Ease of Access` → `Other options` → `Play animations in Windows`.
* Disable `Ease of Access` → `Other options` → `Show Windows background`.

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

### Internet Explorer

#### Search providers

* Remove all pre-existing accelerators.
* Add Google.

#### Accelerators

* Remove all pre-existing accelerators.

#### Tracking Protection

* Add EasyList (AdBlock Plus)

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
