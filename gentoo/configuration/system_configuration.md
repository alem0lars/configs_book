# System configuration

I (and suggest you to) use [`Fizzy`](https://github.com/alem0lars/fizzy) for managing your system configurations.

For me (and for those using `Fizzy`) this step comes for free.

### Install `Fizzy`

To install `Fizzy`, run:

```ShellSession
$ echo "dev-ruby/thor ~amd64" >> "/etc/portage/package.keywords"
$ emerge ruby git thor # Needed by fizzy.
$ curl https://raw.githubusercontent.com/alem0lars/fizzy/master/fizzy | sudo tee /usr/local/bin/fizzy > /dev/null # Install Fizzy into /usr/local/bin/fizzy.
$ chmod +x /usr/local/bin/fizzy
```

### Sync configurations

```ShellSession
$ _configs_url="git@github.com:alem0lars/configs" # Replace with your configurations repository.
$ fizzy cfg sync --url "${_configs_url}"
```

### Create the `system` instance

The `system` instance holds system-wide (as well as `root` user) configurations.

It's instantiated by the root user, so normal users won't be able to modify them without `root` permissions (`Fizzy` security model is so simple that rocks :D).

```ShellSession
$ _inst_name="system" # Replace if you prefer another name (like `root` or something else).
$ _vars_name="julia_hck_gentoo" # Replace with your variables name.
$ fizzy cfg instantiate --vars-name="${_vars_name}" --inst-name="${_inst_name}"
```

### Install the `system` instance

```ShellSession
$ _inst_name="system" # Replace if you prefer another name (like `root` or something else).
$ _vars_name="julia_hck_gentoo" # Replace with your variables name.
$ fizzy sys install --vars-name="${_vars_name}" --inst-name="${_inst_name}"
```
