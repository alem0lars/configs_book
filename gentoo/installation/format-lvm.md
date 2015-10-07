# Format using LVM

## Steps

1. **Create partitions of type `lvm`** (for every partition you want to use).

2. **Create physical volumes**, one for every `lvm` partition you've created in `step (1)`.
 
   For example to create the physical volume for the partition `/dev/mapper/primary`, run:
  
   ```ShellSession
   # pvcreate "/dev/mapper/primary"
   ```

* **Create volume groups**: you have complete choice here (multiple physical volumes can join the same group).
  
  Personally, I prefer to create:
  * A `primary` volume group holding all of the system logical volumes.
  * A `secondary` volume group holding auxiliary logical volumes (like `data` and `vm`).
   
  To create a volume group called `primary` using the physical volume `/dev/mapper/primary`, run:

  ```ShellSession
  # vgcreate "primary" "/dev/mapper/primary"
  ```

* **Create logical volumes**: these fit in the same role of normal partitions in non-LVM setups.

  To create a partition of size `4` gigabytes, inside the volume group `primary`, called `swap`, run:
  
  ```ShellSession
  # lvcreate -L 4G "primary" -n "swap"
  ```
  
  To create a partition that fills all of the available size, inside the volume group `primary`, called `root`, run:
  
  ```ShellSession
  # lvcreate -l +100%FREE "primary" -n "swap"
  ```
  
* **Format the logical volumes**, using `mkfs.*` tools.
