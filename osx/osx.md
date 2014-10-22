# OSX Configuration tutorial

## Some informations

Some script-kiddies can follow the tutorial without knowing what they are actually doing, but the real Hacker wants to know what he's doing.. Here there're some links:
* [How to manage configurations using MR and VCSH](http://www.martin-burger.net/blog/unix-shell/manage-dotfiles-quickly-and-effortlessly/)

## Installation

Create a *encrypted* and *case-sensitive* partition and install OS X on it.

## System setup

### Tweak system preferences

`TODO`

### Create basic directories

* Create the directories:
  
  ```
  $ mkdir ~/Tmp      # Create the temporary directory
  $ mkdir ~/Projects # Create the projects directory
  ```

* Add the directories `~/Tmp`, `~/Projects`, `~/Public` as favorites.

### Setup software

* [HomeBrew](./software/homebrew.md)

* [Git](./software/git.md)

* [SSH](./software/ssh.md)

* [QuickLook](./software/quicklook.md)

* [iTerm 2](./software/iterm2.md)

* [Paragon NTFS](./software/paragon_ntfs.md)

* [ZSH](./software/zsh.md)

* [Google Chrome](./software/google_chrome.md)

* [Moom](./software/moom.md)

* [Copy'em Paste](./software/copyempaste.md)

* [CleanApp](./software/cleanapp.md)

* [Launch Control](./software/launchcontrol.md)

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
