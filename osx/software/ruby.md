# Ruby

## RbEnv

### Installation

```ShellSession
$ brew install ruby-build
$ brew install rbenv
```

### RbEnv extensions

```ShellSession
$ rbenv-bundler
```

## Install

Install the latest stable ruby version (using RbEnv and Ruby-Build)
```ShellSession
$ rbenv install $(rbenv install --list | grep "^\s*[0-9]\.[0-9]\.[0-9]\s*$" | tail -n 1)
```

## Configuration

The configuration should be available through the *VCSH configuration for Ruby* (the [configs-ruby](https://github.com/alem0lars/configs-ruby) repository contents)
