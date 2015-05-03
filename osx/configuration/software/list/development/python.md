# `Python`

## Pyenv

We use `Pyenv` to manage `Python` installations.

### Requirements

* [Package Manager](../system/package_manager.md)

### Installation

```ShellSession
$ brew install pyenv
```

### Extensions

```ShellSession
$ brew install pyenv-which-ext  # https://github.com/yyuu/pyenv-which-ext
```

### VirtualEnv integration

```ShellSession
$ brew install pyenv-virtualenv # https://github.com/yyuu/pyenv-virtualenv
```

## Additional tools

### System-wide packages

By default the `pip` package manager and the `virtualenv` package aren't preinstalled in the system-wide `Python`. They should instead also available system-wide.

#### Installation

```ShellSession
$ sudo easy_install pip
$ sudo pip install virtualenv
```

## Configuration

I use [`Fizzy`](https://github.com/alem0lars/fizzy) to configure `Python`.
The relevant configs are [here](https://github.com/alem0lars/configs/tree/master/python).
