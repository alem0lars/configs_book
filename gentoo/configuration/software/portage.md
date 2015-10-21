# Portage

## Misc tools

```ShellSession
# emerge "app-portage/gentoolkit"
# emerge "app-portage/genlop"
# emerge "app-portage/eix"
# emerge "app-portage/demerge"
```

## Layman

```ShellSession
# emerge "app-portage/layman"
```

Remove and regenerate old cache:

```ShellSession
# rm -rf "/var/cache/edb/dep"
# emerge --metadata
# eix-update
# eix-sync
```
