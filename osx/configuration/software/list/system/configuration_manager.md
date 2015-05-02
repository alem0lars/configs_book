# Configuration Manager

I use [`Fizzy`](https://github.com/alem0lars/fizzy) as configuration manager.

## Requirements

* [Package manager](./package_manager.md)

## Installation

```ShellSession
$ sudo gem install thor # The one and the only Fizzy dependency.
$ brew install fizzy --HEAD # At the moment there isn't a version released yet.
```

## First Sync

```ShellSession
$ _configs_repo="git@github.com:alem0lars/configs" # Replace with your configurations repository.
$ fizzy cfg sync --url="${_configs_repo}"
```

## Instantiate & Install your configurations

```ShellSession
$ _vars_name="julia_osx" # Replace with your variables name.
$ _inst_name="main" # Replace with your instance name.
$ fizzy cfg instantiate --vars-name="${_vars_name}" --inst-name="${_inst_name}"
$ fizzy sys install --vars-name="${_vars_name}" --inst-name="${_inst_name}"
```
