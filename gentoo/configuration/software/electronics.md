# Electronics

## Design

```ShellSession
# emerge "sci-electronics/eagle"
# env-update
# rm -R ~/eagle
```

## PIC development

### Installation notes

Unfortunately Microchip made impossible to create a decent ebuild.

Basically the installer is a tar with inside a shell script (makeself) which
extracts two ELFs to install the software constantly breaking the sandbox by
writing with hardcoded paths all over the system.

Yes, I know *Microchip developers are dumb shits* and IDK why they did such
a shitty installer, but ATM is the only option available.

We need to install it from outside the portage system (yes, I am really sad)
using the standalone way.

I've checked inside the installer and I found which are the external
dependencies. Fortunately, they can all be installed using portage, but
unfortunately when you uninstall mplab you need to manually install those
dependencies.

That's really bad but that's what you get for having stupid people developing
software installers like Microchip ones.

### Dependencies

Install the following libraries (with `32bit` support enabled):

```ShellSession
# emerge "dev-libs/expat[abi_x86_32(-)]"
# emerge "x11-libs/libXext[abi_x86_32(-)]"
# emerge "x11-libs/libX11[abi_x86_32(-)]"
```

### Installation

* Download the installer from
  [here](http://www.microchip.com/mplabx-ide-linux-installer)
* Extract the downloaded archive.
* Run:

  ```ShellSession
  # ./MPLABX-v*-linux-installer.sh
  ```

  As destination folder choose: `/opt/microchip/mplabx/v${version}`, replacing
  ${version} with the version of MPLabX being installed.

### Compilers

You should install the following compilers:

* `XC8`: for `8bit` microcontrollers.
* `XC16`: for `16bit` microcontrollers.
* `XC32`: for `32bit` microcontrollers.

#### Installation

* Download them from
  [here](http://www.microchip.com/pagehandler/en-us/family/mplabx)
* Make installers runnable:

  ```ShellSession
  # chmod +x xc*-v*-full-install-linux-installer.run
  ```

* Install the compilers, by running the installers:

  ```ShellSession
  # ./xc8-v*-full-install-linux-installer.run
  # ./xc16-v*-full-install-linux-installer.run
  # ./xc32-v*-full-install-linux-installer.run

  As destination folder choose: `/opt/microchip/${compilername}/v${version}`,
  replacing:

  * `${compilername}` with the name of the compiler being installed.
  * `${version}` with the version of the compiler being installed.

#### Plugins

Install the following MPLabX plugins:

* SEGGER JLink Probe
* dsPIC Filter Designer
* DMCI
* MPLAB Harmony Configurator
* Power Monitor
* ELFViewer
* MPLABX KeeLoq Plugin
* MPLAB Code Configurator
* Digital Compensator Design Tool Plugin

### Frameworks

#### Microchip Harmony

* Download from the framework from
  [here](http://www.microchip.com/pagehandler/en_us/devtools/mplabharmony/home.html)
* Make the installer runnable:

  ```ShellSession
  # chmod +x harmony_v*_linux_installer.run
  ```

* Install the framework, by running the installer:

  ```ShellSession
  # ./harmony_v*_linux_installer.run
  ```

  As destination folder choose: `/opt/microchip/harmony/v${version}`, replacing
  ${version} with the version of harmony being installed.
