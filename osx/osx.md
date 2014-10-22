# OSX Configuration tutorial

## Some informations

Some script-kiddies can follow the tutorial without knowing what they are actually doing, but the real Hacker wants to know what he's doing.. Here there're some links:
* [How to manage configurations using MR and VCSH](http://www.martin-burger.net/blog/unix-shell/manage-dotfiles-quickly-and-effortlessly/)

## Assumptions

* In the software setup I refer a lot to Lastpass because is where I store my software licenses. Of course you can use that service (I strongly suggest it) but you can just skip that advice and manually insert your license however you want :)

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

* [HomeBrew](software/homebrew.md)
* [Git](software/git.md)
* [SSH](software/ssh.md)
* [QuickLook](software/quicklook.md)
* [iTerm 2](software/iterm2.md)
* [Paragon NTFS](software/paragon_ntfs.md)
* [ZSH](software/zsh.md)
* [Google Chrome](software/google_chrome.md)
* [Moom](software/moom.md)
* [Copy'em Paste](software/copyempaste.md)
* [CleanApp](software/cleanapp.md)
* [LaunchControl](software/launchcontrol.md)
* [Terminal Notifier](software/terminal_notifier.md)
* [pidof](software/pidof.md)
* [hr](software/hr.md)
* [GPG](software/gpg.md)
* [VMware Fusion](software/vmware_fusion.md)
* [VirtualBox](software/virtualbox.md)
* [Vagrant](software/vagrant.md)
* [Chef](software/chef.md)
* [TMux](software/tmux.md)
* [TeamViewer](software/teamviewer.md)
* [Apple Remote Desktop](software/apple_remote_desktop.md)
* [JUMP Desktop](software/jump_desktop.md)
* [Viscosity](software/viscosity.md)
* [Wireshark](software/wireshark.md)
* [TCPFlow](software/tcpflow.md)
* [IPCalc](software/ipcalc.md)
* [TOR](software/tor.md)
* [CheatSheet](software/cheatsheet.md)
* [uTorrent](software/utorrent.md)
* [Transmit](software/transmit.md)
* [Better Rename](software/better_rename.md)
* [Disk Doctor](software/disk_doctor.md)
* [Daisy Disk](software/daisy_disk.md)
* [Better Zip](software/better_zip.md)
* [MacTeX](software/mactex.md)
* [Microsoft Office](software/microsoft_office.md)
* [TeXPad](software/texpad.md)
* [Marked](software/marked.md)
* [iBooks Author](software/ibooks_author.md)
* [OmniGraffle](software/omnigraffle.md)
* [Prizmo](software/prizmo.md)
* [Scrivener](software/scrivener.md)
* [Ulysses](software/ulysses.md)
* [iMovie](software/imovie.md)
* [GarageBand](software/garageband.md)

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
