# Format partitions (old way, without LVM)

Open `parted` (or the partitioning tool of choice) and run:

```ShellSession
# _dev_name="/dev/sda" # Replace with the path of your disk device.
# parted -a optimal "${_dev_name}"
# unit mib # Set MiB as the default unit (the unit to use when no one is specified).
```

For each partition you want to create, do the following:

```
(parted) mkpart primary <FILESYSTEM> <START> <END>
```

where:

* `<FILESYSTEM>`: replace with the filesystem you want to use for that partition
  (e.g. `ext4`, `linux-swap`, etc..).
* `<START>`: the first byte to use. It's the `End` of the previous partition
  (you can see it with the command `print`) *plus `1MiB`* which is `1` because
  the current default unit is `MiB`, for aligning the partitions correctly.
* `<END>`: the last byte to use. You can calculate it as `<START> + <SIZE>`
  where `<SIZE>` is the size you want to give at the partition.

Assign a name to the created partition:

```
(parted) name <NUMBER> <NAME>
```

where:

* `<NUMBER>`: is the partition number. It identifies which partition you want to
  give the name to.
* `<NAME>`: the name to assign to the created partition.

# Assign labels to partitions

Every partition you've created should have a label associated. Doing this,
allows you to find partitions by their label (under `/dev/disk/by-label`).

To do so, see [here](https://wiki.archlinux.org/index.php/Persistent_block_device_naming#by-label)

# Format the partitions


### Format the partitions

Every partition you've created should be formatted, using `mkfs.*` tools.
