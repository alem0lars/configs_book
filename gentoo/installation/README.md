# `Gentoo` Installation

## Setup the installation environment

You'll need Internet connectivity.

## Partitioning

The first step is to create partitions.

Here you have many choices:

1. Create LVM based partitioning layout
2. Create "normal" partitions, without any logical volume management.

In any case, you'll need the following partitions:

1. `root` partition:
  * It will be mounted in `/`.

2. `swap` partition:
  * It will be serve as swapping space.

3. `boot` partition:
  * Holds bootloader informations.
  * You shouldn't have this partition if you have a `UEFI` system.
  * If you haven't an `UEFI` system this partition is *optional*: you can have the `/boot` directory inside the `root` partition instead of having a separate partition. However, creating a separate partition is always preferred.

4. `efi` partition:
  * Holds informations used by the boot-manager and boot-loaders.
  * If you're doing a dualboot setup with `OSX` you already have this partition.

5. `tmp` partition:
  * It will be mounted in `/`.
  * This partition is *optional*: you can have the `/tmp` directory inside the `root` partition or mounted in `RAM`. In that cases you shouldn't have this partition. If you have enough RAM for `/tmp` (it depends, but IMHO `8GB` is enough), then the `RAM` method is preferred.

Of course you can add as many partitions as you want but keep in mind you should create a new partition only if you have a really valid reason to do that, because many partitions have it's drawbacks (resizing partitions is a delicate task).

### Additional resources

If doing a `GNU/Linux`-`OSX` dualboot setup, then read its dedicate [partitioning suggestions](https://github.com/alem0lars/configs_book/blob/master/dualboot_gnulinux_osx/README.md#partitioning-suggestions).
