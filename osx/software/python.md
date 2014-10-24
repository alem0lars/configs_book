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
$ sudo pip install pylint        # Install PyLint
$ sudo pip install pep257        # Install PEP257
$ sudo pip install pep8 autopep8 # Install PEP8 (and related)
$ sudo pip install pygments      # Install Pygments
$ sudo pip install jedi          # Install Jedi
$ sudo pip install ipython       # Install IPython
```

## Configuration

The configuration should be available through the *VCSH configuration for Python* (the [configs-python](https://github.com/alem0lars/configs-python) repository contents)
