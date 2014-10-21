# OSX Configuration tutorial

## Some informations

Some script-kiddies can follow the tutorial without knowing what they are actually doing, but the real Hacker wants to know what he's doing.. Here there're some links:
* [How to manage configurations using MR and VCSH](http://www.martin-burger.net/blog/unix-shell/manage-dotfiles-quickly-and-effortlessly/)


## Installation

Create a *encrypted* and *case-sensitive* partition and install OS X on it.


## System setup


### Tweak system preferences

TODO


### Create basic directories

* Create the directories:
  
  ```
  $ mkdir ~/Tmp      # Create the temporary directory
  $ mkdir ~/Projects # Create the projects directory
  ```

* Add the directories `~/Tmp`, `~/Projects`, `~/Public` as favorites.


### HomeBrew

* Install HomeBrew and HomeBrew Cask:
  
  ```
  $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  $ brew doctor 			                   # Check installation is correct
  $ brew install caskroom/cask/brew-cask # Install HomeBrew Cask
  ```

#### Configuration

* Tap the repositories:
  
  ```
  $ brew tap alem0lars/homebrew-repo     # Add the alem0lars repo
  $ brew tap homebrew/homebrew-science   # Add the science repo
  $ brew tap homebrew/binary             # Add the binary repo
  $ brew tap caskroom/fonts              # Add the fonts repo
  $ brew tap --repair
  ```


### Git

#### Configuration

* Global-wise:
  
  ```
  $ git config --global user.email "molari.alessandro@gmail.com" # Set the global email
  $ git config --global user.name "Alessandro Molari"            # Set the global name
  $ git config --global push.default simple                      # Set the default push policy
  ```


### SSH Key

* Login to LastPass and download the SSH keys:

  * The private key should go under: `~/.ssh/id_rsa`

  * The public key should go under:  `~/.ssh/id_rsa.pub`


### Configuration management

```
$ brew install vcsh mr                                  # Install VCSH and MR
$ vcsh clone git@github.com:alem0lars/configs-mr.git mr # Clone the MR repo
$ mr up                                                 # Install the configurations
```


### Fonts

```
$ brew cask install font-lato # Install the font Lato
```


### QuickLook

#### Extensions

```
$ brew cask install qlcolorcode        --appdir=/Applications
$ brew cask install qlstephen          --appdir=/Applications
$ brew cask install qlmarkdown         --appdir=/Applications
$ brew cask install quicklook-json     --appdir=/Applications
$ brew cask install qlprettypatch      --appdir=/Applications
$ brew cask install quicklook-csv      --appdir=/Applications
$ brew cask install betterzipql        --appdir=/Applications
$ brew cask install webp-quicklook     --appdir=/Applications
$ brew cask install suspicious-package --appdir=/Applications
$ brew cask install provisionql        --appdir=/Applications
$ brew cask install cert-quicklook     --appdir=/Applications
```

#### Configuration

* Enable the text selection in QuickLook:

  ```
  $ defaults write com.apple.finder QLEnableTextSelection -bool true && killall Finder
  ```


### iTerm2

* Install iTerm2:

  ```
  $ brew cask install iterm2 --appdir=/Applications
  ```

#### Configuration

* The configuration should be already available through the vcsh configuration for `iterm2` (the `configs-iterm2` repository contents). You just need to load the preferences within iTerm 2 from `~/.iterm2`

* Make iTerm2 the default terminal, by clicking on: `iTerm 2 ► Make iTerm2 Default Term`


### ZSH

* Install Antigen, the ZSH package manager:
  
  ```
  $ brew install antigen
  ```

#### Configuration

* Set ZSH as the default shell:

  ```
  $ chsh -s /bin/zsh
  ```

* The configuration should be already available through the vcsh configuration for `zsh` (the `configs-zsh` repository contents)


### Paragon NTFS

* Install Paragon NTFS:

  ```
  brew cask install paragon-ntfs --appdir=/Applications
  ```

#### Configuration

* Activate the software using the license stored in Lastpass


### Google Chrome

* Install Google Chrome:
  
  ```
  $ brew cask install google-chrome --appdir=/Applications
  ```

#### Configuration

* Make Google Chrome the default web browser

* Login to sync everything (extensions, settings, etc)


### Moom

* Install from the Mac App Store

#### Configuration

* The configuration should be already available through the vcsh configuration for `moom` (the `configs-moom` repository contents)


### Copy'em Paste

* Install from the Mac App Store

* Install the helper from [http://www.apprywhere.com/copyem-paste-helper.html](http://www.apprywhere.com/copyem-paste-helper.html)

#### Configuration

* Set autostart on login

* Set keybindings:

  * ` ⌥ v`: Show the copy'em paste window


### CleanApp

* Install from [http://www.syniumsoftware.com/cleanapp/](http://www.syniumsoftware.com/cleanapp/)

#### Configuration

* When asked, install the logging service and its preference pane

* Activate the software using the license stored in Lastpass


### LaunchControl

* Install LaunchControl:
  
  ```
  $ brew cask install launchcontrol --appdir=/Applications
  ```


### Terminal Notifier

* Install Terminal Notifier:

  ```
  $ brew install terminal-notifier
  $ brew linkapps
  ```


### pidof

* Install pidof:

  ```
  $ brew install pidof
  ```


### hr

* Install hr:

  ```
  $ brew install hr
  ```


### GPG

* Install hr:

  ```
  $ brew install gpg --8192
  ```


### VMware fusion

### VirtualBox

### Vagrant

* Install:

  ```
  $ brew cask install vagrant vagrant-manager --appdir=/Applications
  ```

### Plugins:

* Plugin for having windows-based vagrant boxes:
  
  ```
  $ sudo vagrant plugin install vagrant-windows
  $ sudo vagrant plugin install vagrant-cachier
  ```

# Configuration

* Set autostart on login for Vagrant Manager

* Change the terminal to iTerm in Vagrant Manager

* Allow automatic updates (to Beta versions) in Vagrant Manager


### Chef

* Install Chef:

  ```
  $ brew cask install chefdk --appdir=/Applications
  ```

* Install the Vagrant plugins:

  ```
  $ sudo vagrant plugin install vagrant-omnibus
  $ sudo vagrant plugin install vagrant-berkshelf
  ```
