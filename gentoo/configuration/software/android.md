# Android

## Installation

```ShellSession
# emerge "dev-util/android-sdk-update-manager"
# emerge "dev-util/android-tools"
```

## Configuration

```ShellSession
# gpasswd -a "alem0lars" "android" # Replace with your user.
```

## Install SDK

Install:
- The `Android` entries you need (including all sub-entries).
- The `Android SDK Tools`, `Android SDK Build Tools` and
  `Android SDK Platform Tools` relative to the installed API levels.
- The `Extra` entry (all sub-entries, except those not compatible with Linux).
