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
    - Select the following features:
      - Java Development
      - Android Development
      - Scala Development Toolkit
      - Groovy Development

## Installation

```ShellSession
# emerge "app-editors/vim"
```

## Set default editor

```ShellSession
# eselect editor list # Shows the available editors.
# eselect editor set 3 # Set the system editor
```
