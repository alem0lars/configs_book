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

```ShellSession
$ cp -a /Volumes/Hardware\ IO\ Tools/*.app /Applications
$ open /Volumes/Hardware\ IO\ Tools/Network\ Link\ Conditioner.prefPane # It will trigger `Network Link Conditioner` installation.
```

### Graphics Tools for Xcode

#### (Optional) Download

If you haven't saved the installer somewhere else, download it from [Apple Developer Center](https://developer.apple.com/downloads/index.action).

#### Installation

```ShellSession
$ cp -a /Volumes/Graphics\ Tools/*.app /Applications
```

## Configuration

I use [`Fizzy`](https://github.com/alem0lars/fizzy) to configure `XCode`.
The relevant configs are [here](https://github.com/alem0lars/configs/tree/master/xcode).
