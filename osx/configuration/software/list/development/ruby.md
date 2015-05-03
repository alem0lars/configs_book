# `Ruby`

We use `Rbenv` to manage ruby installations.

## Requirements

* [Package Manager](../system/package_manager.md)

## Installation

```ShellSession
$ brew install libyaml readline openssl  # Dependencies.
$ brew install ruby-build                # Allow install of custom Ruby versions.
$ brew install rbenv                     # Install Rbenv.
```

## Rbenv extensions

`Rbenv` will become permanently enabled through envvars and initialization in shell session, i.e after you've configured your system.

At the moment, we just need to temporarly enable `Rbenv`:

```ShellSession
$ export RBENV_ROOT=/usr/local/var/rbenv
$ eval "$(rbenv init -)"
```

### Installation

```ShellSession
$ brew install rbenv-gem-rehash   # This plugin runs `rbenv rehash` every time you install or uninstall a gem.
$ brew install rbenv-default-gems # Automatically install gems every time you install a new version of Ruby.
$ brew install rbenv-whatis       # Add `whatis` command, which resolves abbrevations and aliases to full Ruby version identifiers.
$ brew install rbenv-aliases      # Add `alias` command, to create aliases for RbEnv Ruby versions.
$ brew install rbenv-vars         # An RbEnv plugin that safely sets global and per-project environment variables.
```
