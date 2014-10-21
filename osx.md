# Installation

Create a encrypted, case-sensitive partition and install OS X on it.

# System setup

## Tweak system preferences

TODO

## Create basic directories

```
$ mkdir ~/Tmp      # Create the temporary directory
$ mkdir ~/Projects # Create the projects directory
$ #=> Add the directories "~/Tmp", "~/Projects", "~/Public" as favorites
```

## HomeBrew

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew install caskroom/cask/brew-cask # Install HomeBrew Cask
$ brew doctor 			                   # Check installation is correct
$ brew tap alem0lars/homebrew-repo     # Add alem0lars repo
$ brew tap homebrew/homebrew-science   # Add science repo
$ brew tap homebrew/binary             # Add binary repo
$ brew tap caskroom/fonts              # Add fonts repo
$ brew tap --repair && brew update     # Update the formulas
```

## Git

```
$ git config --global user.email "molari.alessandro@gmail.com"
$ git config --global user.name "Alessandro Molari"
```

## Configuration management

```
$ brew install vcsh mr # Install VCSH (and myrepos)
```

## Fonts

```
$ brew cask install font-lato # Install the font Lato
```

## iTerm2

```
$ brew cask install iterm2 --appdir=/Applications # Install iTerm2
$ #=> Make "iTerm2 Default Term"
$ #=> Load the preferences from <iCloud Drive>/Backups/iTerm2
```

## ZSH

```
$ chsh -s /bin/zsh     # Set ZSH as the default shell
$ brew install antigen # Install Antigen, the ZSH package manager
```

## Google Chrome

```
$ brew cask install google-chrome --appdir=/Applications # Install Google Chrome
$ #=> Make Google Chrome the default web browser
$ #=> Login to sync everything (extensions, settings, etc)
```
