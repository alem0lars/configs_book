# `GNU/Linux`-`OSX` dualboot Setup Tutorial

## Steps summary

1. Install `OSX`.
2. Install `GNU/Linux`.
3. Install an `UEFI` boot-loader in `GNU/Linux`.
4. Install the boot-manager (`rEFInd`).
5. Configure your `OSX` installation.
6. Configure your `GNU/Linux` installation.

## Step 1: Install `OSX`

First of all, you need to install a clean version of `OSX` in a smaller partition.

To do so, first [create a bootable USB-drive containing the `OSX` installer](../osx/tips/bootable_usb_installer.md).

1. Start the installer.
5. Run the application `Disk Utility` and create a new partition for OSX (I suggest with Journaling and Encryption), but be sure to leave empty space for `GNU/Linux`.
6. Install `OSX` in the created partition.

## Step 2: Install `GNU/Linux`

**TODO**

## Step 3: Install an `UEFI` boot-loader in `GNU/Linux`

**TODO**

## Step 4: Install the boot-manager (`rEFInd`)

You can install the boot-manager from `OSX` or `GNU/Linux`. However, the [documentation explicitly says](http://rodsbooks.com/refind/installing.html#installsh) you **should** install `rEFInd` from within `OSX`.

Perform the following steps:

1. Login to `OSX`.
2. Go to the [getting.html](http://rodsbooks.com/refind/getting.html) webpage download the binary ZIP, which contains the installation script.
3. Extract the downloaded archive and cd into it.
4. Now you should see a file called `install.sh` which is the installation script.
5. Install `rEFInd` into the `UEFI` volume (called `EFI`), by executing:
   
  ```ShellSession
  $ ./install.sh # From inside the extracted folder.
  ```

## Step 5: Configure your `OSX` installation

**Check out the specific guide for setup your `OSX` installation.**

I use and suggest [this](../osx/README.md).

## Step 6: Configure your `GNU/Linux` installation

**Check out the specific guide for setup your `GNU/Linux` installation.**

I use and suggest [this](../nixos/README.md).
