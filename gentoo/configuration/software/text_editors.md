# Text editors

## Dependencies

- [**Eclipse**](./ide.md) (needed by eclim).
- **Eclim**:

  - Download it from [here](http://sourceforge.net/projects/eclim/files/eclim)
  - Run the installer:

    ```ShellSession
    $ java -jar eclim*.jar
    ```

    Be sure to:

    - Uncheck the option to install vim files.
    - Select all of the available eclipse features.

## Installation

```ShellSession
# emerge "app-editors/vim"
```

## Set default editor

```ShellSession
# eselect editor list # Shows the available editors.
# _editor_number=3 # The vim editor number (possibly called `/usr/bin/vi`).
# eselect editor set ${_editor_number} # Set the system editor.
```
