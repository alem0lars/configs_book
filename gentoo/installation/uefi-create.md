# Create UEFI partition

* Create the EFI partition with label `EFI` of type `EFI` (code: `EF00`) of size at least `512MiB`:

  ```ShellSession
  # gdisk /dev/sda
  Command (? for help): n
  Partition number (1-128, default 1): 1
  First sector (...): <enter>
  Last sector (...): +512M
  Command (? for help): t
  Partition number (1-2): 1
  Hex code or GUID (L to show codes, Enter = 8300): EF00
  Command (? for help): w
  ```

* Format the created partition as `fat32`:

  ```ShellSession
  mkfs.vfat -F 32 /dev/sda1
  ```
