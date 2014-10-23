# Wireshark

## Installation

```ShellSession
$ brew install wireshark --with-lua --with-pcre --with-qt
$ brew linkapps
```

## Capture interface

You need to add the capture interface to be used by Wireshark:
```ShellSession
$ curl "https://bugs.wireshark.org/bugzilla/attachment.cgi?id=3373" -o ~/Downloads/ChmodBPF.tar.gz
$ cd ~/Downloads && tar zxvf ChmodBPF.tar.gz && cd ~
$ open ~/Downloads/ChmodBPF/Install\ ChmodBPF.app
$ rm -R ~/Downloads/ChmodBPF
```
