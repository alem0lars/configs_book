# Text editors

## `Vim`

```ShellSession
$ emerge vim
```

## Set default editor

```ShellSession
$ sudo eselect editor list                  # Shows the available editors.
$ _editor_number=3                          # Replace with the `vim` editor number (possibly called `/usr/bin/vi`).
$ sudo eselect editor set ${_editor_number} # Set the system editor (`EDITOR` environment variable).
```

## Dependencies

If you want to use `eclim`, you should install `Eclipse` and run it in headless
mode.

```ShellSession
# emerge "dev-util/eclipse-sdk-bin"
```
