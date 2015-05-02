# Package Manager

The current best way to manage software (aka packages) is [`Homebrew`](http://brew.sh).

However, by design, it only manages packages in `/usr/local/Cellar` and not standalone applications; for those there is [`Homebrew Cask`](http://caskroom.io) which is an extension to `Homebrew` to also manage application bundles.

## Installation
  
```ShellSession
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew doctor # Check installation is correct
$ brew install caskroom/cask/brew-cask # Install Homebrew Cask
```

## Add repositories
  
```ShellSession
$ brew tap alem0lars/homebrew-repo     # Add the alem0lars repo
$ brew tap homebrew/homebrew-science   # Add the science repo
$ brew tap homebrew/binary             # Add the binary repo
$ brew tap caskroom/fonts              # Add the fonts repo
$ brew tap --repair
```
