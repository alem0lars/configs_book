# Chef

## Installation

```
$ brew cask install chefdk --appdir=/Applications
```

## Vagrant integration

It is provided by the following vagrant plugins (*to install them you also need to have [vagrant installed](vagrant.md)*):
* [vagrant-omnibus](https://github.com/opscode/vagrant-omnibus): A Vagrant plugin that ensures the desired version of Chef is installed via the platform-specific Omnibus packages.
* [vagrant-berkshelf](https://github.com/berkshelf/vagrant-berkshelf): A Vagrant plugin that ensures the desired version of Chef is installed via the platform-specific Omnibus packages.

Install them:
```
$ vagrant plugin install vagrant-omnibus
$ vagrant plugin install vagrant-berkshelf
```
