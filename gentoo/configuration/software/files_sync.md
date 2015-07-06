# Files sync

## Installation

```ShellSession
# emerge "net-misc/megatools"
```

## Check if it's working

Run the following code to check your account quota (i.e. if your client is
working), assuming the name follows the convention: `username @ site`.

```ShellSession
$ _email="molari.alessandro@gmail.com"
$ megadf -u "${_email}" -p $(lpass show --password "${_email} @ mega.co.nz")
```

## Perform sync

Now you can sync selective folders to their respective version online.

### Directories to sync

This is based on your needs / conventions. Mine are:

- `/archive/documents → /Root/documents`

### Sync example

In the following sync example, the local directory `/archive/documents` will
be sync'ed with `/Root/documents` (which is the `documents` folder remotely).

```ShellSession
$ _email="molari.alessandro@gmail.com"
$ _pwd=$(lpass show --password "${_email} @ mega.co.nz")
$ _local_dir="/archive/documents"
$ _remote_dir="/Root/documents"
$ megacopy -d -l ${_local_dir} -r ${_remote_dir} -u "${_email}" -p "${_pwd}"
```
