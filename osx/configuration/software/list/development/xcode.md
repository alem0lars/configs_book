# `Xcode`

## Installation

Install from `Mac App Store`.

## Additional Tools

### XCode Developer Tools

#### Installation

```ShellSession
$ xcode-select --install
```

### Package manager

#### Installation

```ShellSession
$ curl -fsSL https://raw.github.com/supermarin/Alcatraz/master/Scripts/install.sh | sh
```

#### Packages

The following packages should be installed (using Alcatraz):
* CocoaControls
* CocoaPodUI
* FuzzyAutocomplete

### Misc

```ShellSession
$ sudo gem install synx            # Synx, used to align groups with real folders.
$ sudo gem install cocoapods --pre # CocoaPods, used to manage dependencies.
```

### Hardware IO Tools for Xcode

#### (Optional) Download

If you haven't saved the installer somewhere else, download it from [Apple Developer Center](https://developer.apple.com/downloads/index.action).

#### Installation

* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Hardware IO"
  ```
* Copy all of the `.app` files of the downloaded `dmg` into `/Applications/Xcode Tools/Hardware IO`.
* Install `Network Link Conditioner` by double-clicking on `Network Link Conditioner.prefPane`.

### Audio Tools for Xcode

#### (Optional) Download

If you haven't saved the installer somewhere else, download it from [Apple Developer Center](https://developer.apple.com/downloads/index.action).

#### Installation

* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Audio"
  ```
* Copy all of the `.app` files of the downloaded `dmg` into `/Applications/Xcode Tools/Audio`.

### Auxiliary Tools for Xcode

#### (Optional) Download

If you haven't saved the installer somewhere else, download it from [Apple Developer Center](https://developer.apple.com/downloads/index.action).

#### Installation

* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Auxiliary"
  ```
* Copy all of the `.app` files and the directories of the downloaded `dmg` into `/Applications/Xcode Tools/Auxiliary`.

### Graphics Tools for Xcode

#### (Optional) Download

If you haven't saved the installer somewhere else, download it from [Apple Developer Center](https://developer.apple.com/downloads/index.action).

#### Installation

* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Graphics"
  ```
* Copy all of the `.app` files of the downloaded `dmg` into `/Applications/Xcode Tools/Graphics`.

## Configuration

I use [`Fizzy`](https://github.com/alem0lars/fizzy) to configure `XCode`.
The relevant configs are [here](https://github.com/alem0lars/configs/tree/master/xcode).
