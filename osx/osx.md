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

`TODO`

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

* [ImageOptim](software/image_optim.md)
* [Napkin](software/napkin.md)
* [PixelMator](software/pixelmator.md)
* [iDraw](software/idraw.md)
* [Ortelius](software/ortelius.md)

#### Audio

* [GarageBand](software/garageband.md)

#### Video

* [iMovie](software/imovie.md)

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
* [MongoDB](software/mongodb.md)
* [Redis](software/redis.md)
* [PostgreSQL](software/postgresql.md)
* [MySQL](software/mysql.md)
* [Highlight](software/highlight.md)
* [DirEnv](software/direnv.md)

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
