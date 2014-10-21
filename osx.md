# OSX Configuration tutorial

## Some informations

script-kiddies can follow the tutorial without knowing what they are actually doing, but the Hacker wants to know what he's doing, so here are some links:
* [How to manage configurations using MR and VCSH](http://www.martin-burger.net/blog/unix-shell/manage-dotfiles-quickly-and-effortlessly/)


## Installation

Create a encrypted, case-sensitive partition and install OS X on it.


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

* Tap the repositories:
  ```
  $ brew tap alem0lars/homebrew-repo     # Add the alem0lars repo
  $ brew tap homebrew/homebrew-science   # Add the science repo
  $ brew tap homebrew/binary             # Add the binary repo
  $ brew tap caskroom/fonts              # Add the fonts repo
  $ brew tap --repair
  ```


### Git

* Global-wise git configuration:
  ```
  $ git config --global user.email "molari.alessandro@gmail.com" # Set the global email
  $ git config --global user.name "Alessandro Molari"            # Set the global name
  $ git config --global push.default simple                      # Set the default push policy
  ```


### SSH Key

* Login to LastPass and download the SSH keys:
  * The private should go under: `~/.ssh/id_rsa`
  * The public should go under: `~/.ssh/id_rsa.pub`


### Configuration management

```
$ brew install vcsh mr # Install VCSH (and myrepos)
```


### Fonts

```
$ brew cask install font-lato # Install the font Lato
```


### iTerm2

```
$ brew cask install iterm2 --appdir=/Applications # Install iTerm2
$ #=> Make "iTerm2 Default Term"
$ #=> Load the preferences from <iCloud Drive>/Backups/iTerm2
```


### ZSH

```
$ chsh -s /bin/zsh     # Set ZSH as the default shell
$ brew install antigen # Install Antigen, the ZSH package manager
```


### Google Chrome

```
$ brew cask install google-chrome --appdir=/Applications # Install Google Chrome
$ #=> Make Google Chrome the default web browser
$ #=> Login to sync everything (extensions, settings, etc)
```
