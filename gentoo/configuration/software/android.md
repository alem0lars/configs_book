# Android

## Installation

```ShellSession
# emerge "dev-util/android-sdk-update-manager"
```

## Configuration

```ShellSession
# _username="alem0lars" # Replace with your user.
# gpassword -a ${_username} android
```

## Install SDK

Install:
- The latest `Android` entry (all sub-entries).
- The latest `Android M` entry (all sub-entries).
- The `Android SDK Tools`, `Android SDK Build Tools` and `Android SDK Platform Tools` relative to
  the installed API levels.
- The `Extra` entry (all sub-entries, except those not compatible with Linux).
