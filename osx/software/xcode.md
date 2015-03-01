# Xcode

## Installation

Install from Mac App Store

## Tools

### Hardware IO Tools for Xcode

* Download from [Apple Developer Center](https://developer.apple.com/downloads/index.action).
* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Hardware IO"
  ```
* Copy all of the `.app` files of the downloaded `dmg` into `/Applications/Xcode Tools/Hardware IO`.
* Install `Network Link Conditioner` by double-clicking on `Network Link Conditioner.prefPane`.

### Audio Tools for Xcode

* Download from [Apple Developer Center](https://developer.apple.com/downloads/index.action).
* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Audio"
  ```
* Copy all of the `.app` files of the downloaded `dmg` into `/Applications/Xcode Tools/Audio`.

### Auxiliary Tools for Xcode

* Download from [Apple Developer Center](https://developer.apple.com/downloads/index.action).
* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Auxiliary"
  ```
* Copy all of the `.app` files and the directories of the downloaded `dmg` into `/Applications/Xcode Tools/Auxiliary`.

### Graphics Tools for Xcode

* Download from [Apple Developer Center](https://developer.apple.com/downloads/index.action).
* Create a directory for those tools:
  
  ```ShellSession
  $ mkdir "/Applications/Xcode Tools/Graphics"
  ```
* Copy all of the `.app` files of the downloaded `dmg` into `/Applications/Xcode Tools/Graphics`.

## Package manager

### Installation

```ShellSession
$ curl -fsSL https://raw.github.com/supermarin/Alcatraz/master/Scripts/install.sh | sh
```

### Packages

The following packages should be installed (using Alcatraz):
* CocoaControls
* CocoaPodUI
* FuzzyAutocomplete

## Configuration

The configuration should be available through the *VCSH configuration for Xcode* (the [configs-xcode](https://github.com/alem0lars/configs-xcode) repository contents)

* Set `base16-default.dark` as the default theme

## Tools

### Installation

```ShellSession
$ sudo gem install synx            # Synx, used to align groups with real folders.
$ sudo gem install cocoapods --pre # CocoaPods, used to manage dependencies.
```
