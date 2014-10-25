# Python

## System-wide packages

Install the following packages in the system-wide Python:
```ShellSession
$ sudo easy_install pip
$ sudo pip install virtualenv
```

## PyEnv

```ShellSession
$ brew install pyenv
```

### Extensions

```ShellSession
$ brew install pyenv-pip-rehash # https://github.com/yyuu/pyenv-pip-rehash
$ brew install pyenv-which-ext  # https://github.com/yyuu/pyenv-which-ext
```

### VirtualEnv integration

```ShellSession
$ brew install pyenv-virtualenv # https://github.com/yyuu/pyenv-virtualenv
```

## VirtualEnvs

The following VirtualEnvs are always suggested:
* `misc`: Used to develop and test miscellaneous stuff and scripts

### Installation

```ShellSession
$ pyenv virtualenv misc # Install the Misc VirtualEnv
```

## Development tools

The development tools should be installed system-wide

```ShellSession
$ sudo pip2 install pylint pep257 pep8 autopep8 pygments jedi ipython # Install on system-wide Python 2
$ sudo pip3 install pylint pep257 pep8 autopep8 pygments jedi ipython # Install on system-wide Python 3
```

## Configuration

The configuration should be available through the *VCSH configuration for Python* (the [configs-python](https://github.com/alem0lars/configs-python) repository contents)

### PATH

Prepend the following lines to `/etc/paths`:
* `/usr/local/opt/pyenv/shims`
* `/usr/local/opt/pyenv/bin`
