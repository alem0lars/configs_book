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
