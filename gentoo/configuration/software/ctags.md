# `ctags`

## `Exhuberant Ctags`

### Installation

```ShellSession
# emerge "dev-util/ctags"
# emerge "app-eselect/eselect-ctags"
```

## Select the `etags` target

```ShellSession
# eselect etags list      # Show available etags targets.
# _n=1                    # The number associated to the etags target you want.
# eselect etags set ${_n} # Set the etags target system-wide.
```