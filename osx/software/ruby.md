# Ruby

## RbEnv

### Installation

```ShellSession
$ brew install libyaml readline openssl  # Dependencies.
$ brew install ruby-build                # Allow install of custom Ruby versions.
$ brew install rbenv                     # Install RbEnv.
```

### RbEnv extensions

```ShellSession
$ brew install rbenv-gem-rehash   # This plugin runs `rbenv rehash` every time you install or uninstall a gem.
$ brew install rbenv-default-gems # Automatically install gems every time you install a new version of Ruby.
$ brew install rbenv-whatis       # Add `whatis` command, which resolves abbrevations and aliases to full Ruby version identifiers.
$ brew install rbenv-aliases      # Add `alias` command, to create aliases for RbEnv Ruby versions.
$ brew install rbenv-vars         # An RbEnv plugin that safely sets global and per-project environment variables.
```

## Install

Install the latest stable ruby version (using RbEnv and Ruby-Build)
```ShellSession
$ RUBY_CONFIGURE_OPTS="--with-openssl-dir=`brew --prefix openssl` --with-readline-dir=`brew --prefix readline` --with-libyaml-dir=`brew --prefix libyaml`" rbenv install $(rbenv install --list | grep "^\s*[0-9]\.[0-9]\.[0-9]\s*$" | tail -n 1)
```

## Development tools

```ShellSession
$ sudo gem install haml
```

## Configuration

The configuration should be available through the *VCSH configuration for Ruby* (the [configs-ruby](https://github.com/alem0lars/configs-ruby) repository contents)

### PATH

Prepend the following lines to `/etc/paths`:
* `/usr/local/opt/rbenv/shims`
* `/usr/local/opt/rbenv/bin`

### Dependencies

#### IRB

Install the IRB configuration (`.irbrc`) dependencies:
```ShellSession
$ sudo gem install methodfinder bond sketches awesome_print wirble looksee hirb what_methods net-http-spy ori clipboard coderay
```
