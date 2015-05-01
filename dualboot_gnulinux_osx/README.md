# `GNU/Linux`-`OSX` dualboot Setup Tutorial

## Steps summary

1. Install `OSX`.
2. Install `GNU/Linux`.
3. Install the boot-manager (`rEFInd`).
4. Configure your `OSX` installation.
5. Configure your `GNU/Linux` installation.

## Step 1: Install `OSX`

First of all, you need to install a clean version of `OSX` in a smaller partition.

To do so, first [create a bootable USB-drive containing the `OSX` installer](../osx/tips/bootable_usb_installer.md).

Then:

1. Start the installer.
2. Run the application `Disk Utility` and create a new partition for OSX (I suggest with Journaling and Encryption), but be sure to leave empty space for `GNU/Linux`.
3. Install `OSX` in the created partition.

## Step 2: Install `GNU/Linux`

After installing `OSX`, you need to install the other OS, which is `GNU/Linux`.
Note that you also need a `UEFI` boot-loader (since `rEFInd` is a boot-manager, not a boot-loader). `OSX` already includes it's own boot-loader, but in `GNU/Linux` you need to explicitly install it in the `EFI` partition.

I use and suggest [this](../nixos/installation/README.md).

## Step 3: Install the boot-manager (`rEFInd`)

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

### Customizations

First of all, you need to mount the `EFI` partition, which contains among other things the `rEFInd` configuration. One way is to enable the `Debug` menu in `Disk Utility` and mount the partition called `EFI`.

#### Change theme

To install a custom theme, perform the following steps:

1. Choose a theme.
   [Here](http://rodsbooks.com/refind/themes.html) is a list of some.
   IMHO good ones are:
   * [`rEFInd minimal`](https://github.com/EvanPurkhiser/rEFInd-minimal).
   * [`Regular rEFInd`](http://munlik.deviantart.com/art/Regular-rEFInd-theme-512091944).
1. Download and extract it.
2. Copy the extracted folder inside `/Volumes/EFI/EFI/refind`
3. Add the line `include <THEME_NAME>/theme.conf` in `/Volumes/EFI/EFI/refind/refind.conf` just before the first `menuentry` definition (`<THEME_NAME>` is the name of your theme (the folder's name)).

For example, I picked `rEFInd minimal` and I did the following:

```ShellSession
$ _theme_src_dir="${HOME}/Downloads/refind-minimal" # Directory that holds the theme.
$ cp -a ${_theme_src_dir} /Volumes/EFI/EFI/refind/$(basename $_theme_src_dir)
```

Now reboot and check if the theme is showing correctly.

#### Adjust the options

[Here](http://www.rodsbooks.com/refind/configfile.html#adjusting) is a complete list of the available options.

I advise you to store the file somewhere ([like me]()), so this step involves just in replacing the default configuration file to yours:

```ShellSession
$ curl https://raw.githubusercontent.com/alem0lars/configs/plain/refind/refind_julia.conf > refind.conf
$ mv refind.conf /Volumes/EFI/EFI/refind/refind.conf
```

## Step 5: Configure your `OSX` installation

**Check out the specific guide for setup your `OSX` installation.**

I use and suggest [this](../osx/README.md).

## Step 6: Configure your `GNU/Linux` installation

**Check out the specific guide for setup your `GNU/Linux` installation.**

I use and suggest [this](../nixos/configuration/README.md).
