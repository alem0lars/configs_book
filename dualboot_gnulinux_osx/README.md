# `GNU/Linux`-`OSX` dualboot Setup Tutorial

## Steps summary

1. Install `OSX`.
2. Install `GNU/Linux`.
3. Install the boot-manager (`rEFInd`).
4. Configure your `OSX` installation.
5. Configure your `GNU/Linux` installation.

## Step 1: Install `OSX`

Keep in mind two important things:

1. It's strongly suggested to install a clean version of `OSX`, i.e. use an external installer, like a `OSX` installer in a bootable USB-drive.
2. When partitioning, *be sure to leave empty space for `GNU/Linux`*.

**Check out the specific guide for installing `OSX`.**

I use and suggest [this](../osx/installation/README.md).

## Step 2: Install `GNU/Linux`

After installing `OSX`, you need to install the other OS, which is `GNU/Linux`.
Note that you also need a `UEFI` boot-loader (since `rEFInd` is a boot-manager, not a boot-loader). `OSX` already includes it's own boot-loader, but in `GNU/Linux` you need to explicitly install it in the `EFI` partition.

**Check out the specific guide for installing `GNU/Linux`.**

I use and suggest [this](../gentoo/installation/README.md).

### Additional notes

#### Partitioning suggestions

When performing partitioning I suggest to just use the following parititons:

1. `root` (mounted in `/`)
2. `swap`

This is because *you don't need `boot`* (it's an `UEFI` system).

I suggest mounting `/tmp` in `RAM` (usually `RAM` available in `Mac`s is enough).

For other partitions, like `var`, `home`, etc.. I suggest you to *not create them*, because available space is not so much and dualboot setups are complicate, we want to not extend the complexity for getting almost nothing in advantage.

For example, I have the following partitioning:

| Number |   Start   |   End     | Size      | File system | Name                 | Flags |
|--------|-----------|-----------|-----------|-------------|----------------------|-------|
|   1    | 0.02MiB   | 200MiB    | 200MiB    |    fat32    | EFI System Partition |  boot |
|   2    | 200MiB    | 96126MiB  | 96126MiB  |             | Julia Main Disk      |       |
|   3    | 96126MiB  | 96746MiB  | 620MiB    |    hfs+     | Recovery HD          |       |
|   4    | 96747MiB  | 100747MiB | 4000MiB   |             | gnulinux_swap        |       |
|   5    | 100748MiB | 200748MiB | 100000MiB |             | gnulinux_root        |       | 
|   6    | 200749MiB | 239372MiB | 38623MiB  |             | archive              |       |

### Kernel configuration

When configuring your kernel you should keep in mind your specific hardware (e.g. MacBook pro).

You'll need to enable the [specific kernel options](https://wiki.gentoo.org/wiki/Apple_Macbook_Pro_Retina#Kernel_Configuration)

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
  $ sudo bless --mount /Volumes/EFI --setBoot --file /Volumes/EFI/EFI/refind/refind_x64.efi --shortform
  ```

### Customizations

First of all, you need to mount the `EFI` partition, which contains among other things the `rEFInd` configuration. One way is to enable the `Debug` menu in `Disk Utility` and mount the partition called `EFI`.

#### Adjust options

Before configuring `rEFInd`, perform initial cleanup:

```ShellSession
$ _refind_dir="/Volumes/EFI/EFI/refind"
$ rm -R ${_refind_dir}/._*
$ rm -R ${_refind_dir}/font
$ rm -R ${_refind_dir}/icons
$ rm -R ${_refind_dir}/theme
$ rm ${_refind_dir}/bg.png
$ rm ${_refind_dir}/selection-small.png
$ rm ${_refind_dir}/selection-big.png
$ rm ${_refind_dir}/theme.conf
$ rm ${_refind_dir}/Thumbs.db
```

Now you should have just few files/folder there, like `keys`, `drivers_x64`, `refind_x64.efi`, `refind.conf`.

Now you can configure rEFInd:

[Here](http://www.rodsbooks.com/refind/configfile.html#adjusting) is a complete list of the available options.

*I advise you to store the configuration somewhere ([like me](https://github.com/alem0lars/configs/tree/master/refind)).*

##### Using `Fizzy`

I use `Fizzy` to manage the configurations and even if `rEFInd` is different from normal software, if `Fizzy` is powerful enough it should be able to still semi-manage `rEFInd`.

I'm saying semi-manage because the nature of `rEFInd` is really different than normal software. It's in a separate partition (`EFI`), possibly available only at boot time, when other partitions aren't already (and can't be) mounted. This means you can instantiate but not install `rEFInd` configuration. To install the instance you just copy the artifacts into the destination folder.

Let's proceed..

At this stage probably you don't have `Fizzy` installed, I suggest you to temporarly install it and then remove it:

```ShellSession
$ gem install thor --user-install
$ curl https://raw.githubusercontent.com/alem0lars/fizzy/master/fizzy > ${HOME}/fizzy
$ chmod +x ${HOME}/fizzy
```

Now I can instantiate the `rEFInd` configuration:

```ShellSession
$ _inst_name="dualboot_gnulinux_osx"
$ _vars_name="julia_dualboot"
$ ./fizzy cfg instantiate --vars-name="${_vars_name}" --inst-name="${_inst_name}" # Assuming you're in ${HOME}.
$ ./fizzy inst cd "${_inst_name}" # Assuming you're in ${HOME}.
$ cp -a refind/* /Volumes/EFI/EFI/refind
```

After having instantiated the `rEFInd` configuraton you can safely remove `Fizzy` and its dependencies:

```ShellSession
$ ./fizzy cfg cleanup # Assuming you're in ${HOME}.
$ rm ${HOME}/fizzy
$ gem uninstall thor
$ rm -R ${HOME}/.gem # (Optional) This cleans up all gems user installation, safe if you hadn't installed gems before.
```

This is because I want to keep setup stages clean and separate and at this time you shouldn't already configure your system (which includes installing `Fizzy`).

#### (Optional) Choose theme

*I personally don't need a theme, since it's already [included](https://github.com/alem0lars/configs/tree/master/refind/theme) in my `rEFInd` configuration. Even if I had one, it would be already being setup by the step before (using `Fizzy`).*

Anyways, if you want one, to install a custom theme, perform the following steps:

1. Choose a theme.
   [Here](http://rodsbooks.com/refind/themes.html) is a list of some.
   IMHO good ones are:
   * [`rEFInd minimal`](https://github.com/EvanPurkhiser/rEFInd-minimal).
   * [`Regular rEFInd`](http://munlik.deviantart.com/art/Regular-rEFInd-theme-512091944).
1. Download and extract it.
2. Copy the extracted folder inside `/Volumes/EFI/EFI/refind`
3. Add the line `include <THEME_NAME>/theme.conf` in `/Volumes/EFI/EFI/refind/refind.conf` just before the first `menuentry` definition (`<THEME_NAME>` is the name of your theme (the folder's name)).

Now reboot and check the adjustments.

## Step 5: Configure your `OSX` installation

**Check out the specific guide for configuring your `OSX` installation.**

I use and suggest [this](../osx/configuration/README.md).

## Step 6: Configure your `GNU/Linux` installation

**Check out the specific guide for configuring your `GNU/Linux` installation.**

I use and suggest [this](../gentoo/configuration/README.md).
