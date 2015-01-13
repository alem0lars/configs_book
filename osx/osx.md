# OSX Configuration tutorial

## Some informations

Some script-kiddies can follow the tutorial without knowing what they are actually doing, but the real Hacker wants to know what he's doing.. Here there're some links:
* [How to manage configurations using MR and VCSH](http://www.martin-burger.net/blog/unix-shell/manage-dotfiles-quickly-and-effortlessly/)

Some instructions on how to add a configuration [here](https://gist.github.com/alem0lars/d04f497cbb8c1b46be02)

## Assumptions

* In the software setup I refer a lot to Lastpass because is where I store my software licenses. Of course you can use that service (I strongly suggest it) but you can just skip that advice and manually insert your license however you want :)

## Installation

Create a *encrypted* and *case-sensitive* partition and install OS X on it.

## System setup

### Tweak system preferences

#### Boot setup

```ShellSession
$ sudo nvram SystemAudioVolume=" " # Disable the sound effects on boot
```

#### Computer name

In the following lines substitute `julia` with your computer name (`julia` is my ❤)

```ShellSession
$ _computer_name="julia"
$ sudo scutil --set ComputerName ${_computer_name}
$ sudo scutil --set HostName ${_computer_name}
$ sudo scutil --set LocalHostName ${_computer_name}
$ sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.smb.server NetBIOSName -string ${_computer_name}
```

#### Behaviour

* Expand save panel by default

  ```ShellSession
  $ defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode -bool true
  $ defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode2 -bool true
  ```

* Expand print panel by default

  ```ShellSession
  $ defaults write NSGlobalDomain PMPrintingExpandedStateForPrint -bool true
  $ defaults write NSGlobalDomain PMPrintingExpandedStateForPrint2 -bool true
  ```

* Automatically quit printer app once the print jobs complete

  ```ShellSession
  $ defaults write com.apple.print.PrintingPrefs "Quit When Finished" -bool true
  ```

* Disable Resume system-wide

  ```ShellSession
  $ defaults write com.apple.systempreferences NSQuitAlwaysKeepsWindows -bool false
  ```

* Disable the crash reporter

  ```ShellSession
  $ defaults write com.apple.CrashReporter DialogType -string "none"
  ```

* Set Help Viewer windows to non-floating mode

  ```ShellSession
  $ defaults write com.apple.helpviewer DevMode -bool true
  ```

* Restart automatically if the computer freezes

  ```ShellSession
  $ sudo systemsetup -setrestartfreeze on
  ```

* Enable keyboard repeating

  ```ShellSession
  $ defaults write -g ApplePressAndHoldEnabled -bool false
  ```
  
* Remap Caps Lock to Control:
  Go to `` → `System Preferences` → `Keyboard` → `Modifier Keys...` and select Control for Caps Lock.

#### Appearance

* Set sidebar icon size to medium

  ```ShellSession
  $ defaults write NSGlobalDomain NSTableViewDefaultSizeMode -int 1
  ```

* When to show scrollbars

  ```ShellSession
  $ defaults write NSGlobalDomain AppleShowScrollBars -string "Always"
  ```

* Increase window resize speed

  ```ShellSession
  $ defaults write NSGlobalDomain NSWindowResizeTime -float 0.001
  ```

* Disable Mission Control animations

  ```ShellSession
  $ defaults write com.apple.dock expose-animation-duration -float 0
  $ killall Dock # Apply changes
  ```

* Disable Dock animations

  ```ShellSession
  $ defaults write com.apple.dock autohide-time-modifier -float 0
  $ defaults write com.apple.dock autohide-delay -float 0
  $ killall Dock # Apply changes
  ```

* Disable the Launchpad animations

  ```ShellSession
  $ defaults write com.apple.dock springboard-show-duration -float 0 # on showing
  $ defaults write com.apple.dock springboard-hide-duration -float 0 # on hiding
  $ defaults write com.apple.dock springboard-page-duration -float 0 # on changing pages
  $ killall Dock # Apply changes
  ```

* Disable Finder animations

  ```ShellSession
  $ defaults write com.apple.finder DisableAllAnimations -bool true
  $ killall Finder # Apply changes
  ```

* Disable Mail animations

  ```ShellSession
  $ defaults write com.apple.Mail DisableSendAnimations -bool true  # sending messages
  $ defaults write com.apple.Mail DisableReplyAnimations -bool true # opening windows for replies
  ```

`TODO`: Finish

### Create basic directories

* Create the directories:

  ```
  $ mkdir ~/Tmp      # Create the temporary directory
  $ mkdir ~/Projects # Create the projects directory
  ```

* Add the directories `~/Tmp`, `~/Projects`, `~/Public` as favorites.

### Setup software

#### System

* [HomeBrew](software/homebrew.md)
* [Paragon NTFS](software/paragon_ntfs.md)
* [QuickLook](software/quicklook.md)
* [CheatSheet](software/cheatsheet.md)
* [Moom](software/moom.md)
* [Amethyst](software/amethyst.md)
* [Copy'em Paste](software/copyempaste.md)
* [iTerm 2](software/iterm2.md)
* [ZSH](software/zsh.md)
* [pidof](software/pidof.md)
* [hr](software/hr.md)
* [Terminal Notifier](software/terminal_notifier.md)
* [GPG](software/gpg.md)
* [Chef](software/chef.md)
* [TMux](software/tmux.md)
* [Pushover](software/pushover.md)
* [proctools](software/proctools.md)
* [pstree](software/pstree.md)
* [ncdu](software/ncdu.md)
* [KeyCastr](software/keycastr.md)
* [Aewan](software/aewan.md)
* [Keyboard Maestro](software/keyboard_maestro.md)
* [Adobe Air](software/adobe_air.md)

#### Management

* [LaunchControl](software/launchcontrol.md)
* [CleanApp](software/cleanapp.md)

#### Virtualization

* [VMware Fusion](software/vmware_fusion.md)
* [VirtualBox](software/virtualbox.md)
* [Vagrant](software/vagrant.md)

#### Remote Access

* [SSH](software/ssh.md)
* [TeamViewer](software/teamviewer.md)
* [Apple Remote Desktop](software/apple_remote_desktop.md)
* [JUMP Desktop](software/jump_desktop.md)

#### Net Tools

* [Viscosity](software/viscosity.md)
* [Wireshark](software/wireshark.md)
* [TCPFlow](software/tcpflow.md)
* [IPCalc](software/ipcalc.md)
* [TOR](software/tor.md)
* [p0f](software/p0f.md)
* [vnstat](software/vnstat.md)
* [httpie](software/httpie.md)

#### Files

* [uTorrent](software/utorrent.md)
* [Transmit](software/transmit.md)
* [Better Rename](software/better_rename.md)
* [Disk Doctor](software/disk_doctor.md)
* [Daisy Disk](software/daisy_disk.md)
* [Better Zip](software/better_zip.md)

#### Office

* [MacTeX](software/mactex.md)
* [Microsoft Office](software/microsoft_office.md)
* [TeXPad](software/texpad.md)
* [Marked](software/marked.md)
* [iBooks Author](software/ibooks_author.md)
* [OmniGraffle](software/omnigraffle.md)
* [Prizmo](software/prizmo.md)
* [Scrivener](software/scrivener.md)
* [Ulysses](software/ulysses.md)

#### Graphics

* [ImageMagick](software/imagemagick.md)
* [ImageOptim](software/image_optim.md)
* [Icon Slate](software/icon_slate.md)
* [Napkin](software/napkin.md)
* [PixelMator](software/pixelmator.md)
* [iDraw](software/idraw.md)
* [Ortelius](software/ortelius.md)

#### Audio

* [GarageBand](software/garageband.md)

#### Video

* [iMovie](software/imovie.md)
* [VLC](software/vlc.md)

#### Science

* [PocketCAS](software/pocketcas.md)

#### Development

* [Git](software/git.md)
* [Mercurial](software/mercurial.md)
* [Subversion](software/subversion.md)
* [Dash](software/dash.md)
* [Xcode](software/xcode.md)
* [Vim](software/vim.md)
* [Kaleidoscope](software/kaleidoscope.md)
* [Oyster](software/oyster.md)
* [Paw HTTP Client](software/paw_http_client.md)
* [Synalyze It! Pro](software/synalyze_it.md)
* [xScope](software/xscope.md)
* [RHC](software/rhc.md)
* [JDK](software/jdk.md)
* [Python](software/python.md)
* [Ruby](software/ruby.md)
* [Haskell](software/haskell.md)
* [NodeJS](software/nodejs.md)
* [Scala](software/scala.md)
* [Erlang](software/erlang.md)
* [Elixir](software/elixir.md)
* [Groovy](software/groovy.md)
* [C](software/c.md)
* [Rust](software/rust.md)
* [MongoDB](software/mongodb.md)
* [Redis](software/redis.md)
* [PostgreSQL](software/postgresql.md)
* [MySQL](software/mysql.md)
* [Highlight](software/highlight.md)
* [DirEnv](software/direnv.md)
* [Radare](software/radare.md)
* [SQLMap](software/sqlmap.md)
* [jQ](software/jq.md)
* [Sublime Text](software/sublime_text.md)
* [Pow](software/pow.md)
* [IntelliJ IDEA](software/intellij_idea.md)

#### Reading

* [Kindle](software/kindle.md)
* [PDFToolkit+](software/pdftoolkit_plus.md)
* [MetaPDF](software/meta_pdf.md)

#### Social

* [Twitter](software/twitter.md)
* [Textual](software/textual.md)
* [Telegram](software/telegram.md)
* [Skype](software/skype.md)
* [Mumble](software/mumble.md)

#### Reference

* [Safari](software/safari.md)
* [Google Chrome](software/google_chrome.md)
* [iTranslate](software/itranslate.md)

#### Organizer

* [OmniFocus](software/omnifocus.md)
* [Toggl Desktop](software/toggl_desktop.md)

#### Gaming

* [Steam](software/steam.md)
* [OpenEmu](software/openemu.md)

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
