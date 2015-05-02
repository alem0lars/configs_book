# OSX Configuration

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

## Applications.

Now you need to install and configure the applications.

You can choose various applications sets, based on your needs.

[Here]() you can find a list of all available application installation and configuration tutorials.

I suggest you to not install all of them, but choose an application set and install the applications included in.

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