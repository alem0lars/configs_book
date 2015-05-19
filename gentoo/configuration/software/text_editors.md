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
