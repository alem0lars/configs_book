# `Ruby`

## Rbenv

We use `Rbenv` to manage ruby installations.

### Requirements

* [Package Manager](../system/package_manager.md)

### Installation

Before installing `Ruby` you need to install the `Ruby` installer, which is `Rbenv`.
In fact, it will manage `Ruby` versions easily and allows you to install new ones relying on `ruby-build`.

```ShellSession
$ brew install libyaml readline openssl  # Dependencies.
$ brew install ruby-build                # Allow install of custom Ruby versions.
$ brew install rbenv                     # Install Rbenv.
```

### Extensions

`Rbenv` will become permanently enabled through envvars and initialization in shell session, i.e after you've configured your system.

At the moment, we just need to temporarly enable `Rbenv`:

```ShellSession
$ export RBENV_ROOT=/usr/local/var/rbenv
$ eval "$(rbenv init -)"
```

#### Installation

```ShellSession
$ brew install rbenv-gem-rehash   # This plugin runs `rbenv rehash` every time you install or uninstall a gem.
$ brew install rbenv-default-gems # Automatically install gems every time you install a new version of Ruby.
$ brew install rbenv-whatis       # Add `whatis` command, which resolves abbrevations and aliases to full Ruby version identifiers.
$ brew install rbenv-aliases      # Add `alias` command, to create aliases for RbEnv Ruby versions.
$ brew install rbenv-vars         # An RbEnv plugin that safely sets global and per-project environment variables.
```

## Additional tools

Gems (like `irbtools` and `irbtools-more`) will be automatically available in any new version of ruby you will install with Rbenv if you use `rbenv-default-gems` and you've added those to the file `~/.rbenv/default-gems`, [like I did](https://github.com/alem0lars/configs/blob/master/ruby/rbenv-default-gems.tt).

However in the system-wide version of `Ruby` (the one that comes preinstalled in `OSX`) you need to manually install them:

```ShellSession
$ sudo gem install irbtools irbtools-more
```

## Configuration

I use [`Fizzy`](https://github.com/alem0lars/fizzy) to configure `Ruby`.
The relevant configs are [here](https://github.com/alem0lars/configs/tree/master/ruby).