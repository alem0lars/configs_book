# Create encrypted partition

To encrypt (password-based) the partition `/dev/sdaX`, run:

```ShellSession
# cryptsetup luksFormat `/dev/sdaX`
```

And enter the encryption password twice.

# Mount an encrypted partition

To mount the encrypted partition `dev/sdaX` mapped in `/dev/mapper/primary`, where `primary` is the mapping name (you can choose any name), run:

```ShellSession
# cryptsetup open --type luks "/dev/sdaX" "primary"
```

And enter the encryption password.

# Mount an encrypted volume at boot time

Edit `/etc/crypttab`:

```
<MAPPING_NAME> UUID=<DEVICE_UUID> none luks,timeout=180
```
