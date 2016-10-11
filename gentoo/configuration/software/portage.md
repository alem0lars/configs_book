# Portage

## Setup groups

```ShellSession
# gpasswd -a "alem0lars" "portage"
```

## ElogV

```ShellSession
# emerge "app-portage/elogv"
# chown portage:portage "/var/log/portage/elog"
```

## Layman

```ShellSession
# emerge "app-portage/layman"
```

## Eix

```ShellSession
# emerge "app-portage/eix"
```

Remove and regenerate old cache:

```ShellSession
# rm -rf "/var/cache/edb/dep"
# emerge --metadata
# eix-update
# eix-sync
```

## Misc tools

```ShellSession
# emerge "app-portage/gentoolkit"
# emerge "app-portage/genlop"
# emerge "app-portage/demerge"
# emerge "app-portage/euscan"
# emerge "app-portage/metagen"
# emerge "app-portage/portpeek"
# emerge "app-admin/eclean-kernel"
```
