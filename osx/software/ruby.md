# Ruby

## RbEnv

### Installation

```ShellSession
$ brew install readline   # Use ReadLine instead of EditLine
$ brew install ruby-build # Allow install of custom Ruby versions
$ brew install rbenv      # Install RbEnv
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
