# `GNU/Linux`-`OSX` dualboot Setup Tutorial

## Steps summary

1. Install `OSX`.
2. Install `GNU/Linux`.
3. Install an UEFI boot-loader in `GNU/Linux`.
4. Install the boot-manager (`rEFInd`).
5. Configure your `OSX` installation.
6. Configure your `GNU/Linux` installation.

## Step 1: Install `OSX`

First of all, you need to install a clean version of `OSX` in a smaller partition.

To do so, first create a bootable USB-drive containing the `OSX` installer:

1. If you didn't already do, download the latest version of the `OSX` installer from the `Mac App Store`.
2. Format the USB-pen with FAT filesystem and give it a name (e.g. `Install OSX`).
3. Burn it in a USB-pen by running:

  ```ShellSession
  $ _usb_volume_path="/Volumes/Install OSX" # Substitute with your USB-pen volume path.
  $ sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume "${_usb_volume_path}" --applicationpath /Applications/Install\ OS\ X\ Yosemite.app --nointeraction
  ```

4. Boot the USB-pen and start the installer.
5. Run the application `Disk Utility` and create a new partition for OSX (I suggest with Journaling and Encryption), but be sure to leave empty space for `GNU/Linux`.
6. Install `OSX` in the created partition.

## Step 2: Install `GNU/Linux`

**TODO**

## Step 3: Install an UEFI boot-loader in `GNU/Linux`

**TODO**

## Step 4: Install the boot-manager (`rEFInd`)

**TODO**

## Step 5: Configure your `OSX` installation

**Check out the specific guide for setup your `OSX` installation.**

I use and suggest [this](../osx/README.md).

## Step 6: Configure your `GNU/Linux` installation

**Check out the specific guide for setup your `GNU/Linux` installation.**

I use and suggest [this](../nixos/README.md).
