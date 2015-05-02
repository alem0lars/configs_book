# `OSX` Configuration

## System-wide

First of all you should set your system-wide configurations.

Execute the script: [`configure_system`](https://github.com/alem0lars/chips/blob/master/scripts/osx/configure_system):

```ShellSession
$ curl https://raw.githubusercontent.com/alem0lars/chips/master/scripts/osx/configure_system > configure_system
$ chmod +x ./configure_system
$ ./configure_system
$ rm ./configure_system
```

Note that's my system configuration, but *you can adapt it to meet your needs*.

## Software.

Now you need to install and configure the various software.

I suggest you to not install [all of them](./software/list), but choose a [software set](./software/sets) based on your needs and install the applications included in.

Since I'm a minimalistic man and I run `OSX` just for `Cocoa`/`iOS` development or for developing things not available in `GNU/Linux`, I'm currently using [this software set](./software/sets/minimal_development.md).

If you prefer to not follow a particular set, you can just install and configure the software you want. [Here](./software/list) you can find a list of all availables.

Keep in mind some softwares aren't named by the application or library name but by its purpose, so when the concrete solution becomes obsolete we just substitute it with another one, without changing the references. It's also more viable to you to find what you need (sometimes you don't know the applications or libraries names before).

## Fonts

TODO: FIX

```ShellSession
$ brew cask install font-lato # Install the font Lato
```

## Troubleshooting

* Check [here](http://support.apple.com/kb/PH18761) if your Mac is too slow with Yosemite. Also consider removing the `windowserver.plist` files:
  ```ShellSession
  $ sudo rm /Library/Preferences/com.apple.windowserver.plist
  $ rm /Library/Preferences/com.apple.windowserver.plist
  ```
