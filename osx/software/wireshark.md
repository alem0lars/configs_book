# Wireshark

## Installation

```
$ brew install wireshark --with-lua --with-pcre --with-qt
$ brew linkapps
```

## Add the capture interface

```
curl "https://bugs.wireshark.org/bugzilla/attachment.cgi?id=3373" -o ~/Downloads/ChmodBPF.tar.gz
cd ~/Downloads && tar zxvf ChmodBPF.tar.gz && cd ~
open ~/Downloads/ChmodBPF/Install\ ChmodBPF.app

```
