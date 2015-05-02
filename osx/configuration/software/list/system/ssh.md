# SSH

## Configuration

### SSH Key

Install the SSH keys:
* The private key should go under: `~/.ssh/id_rsa`
* The public key should go under:  `~/.ssh/id_rsa.pub`

I and suggest you to keep SSH keys in `LastPass`.

Now secure the keys:

```ShellSession
$ chmod 600 ~/.ssh/id_rsa
$ chmod 600 ~/.ssh/id_rsa.pub
```

## Additional tools

### `Mosh`

[`Mosh`](https://mosh.mit.edu) is an alternative to the SSH protocol relying on `UDP` instead of `TCP`.

I generally prefer `Mosh` to SSH but no all servers (only a few) has the `Mosh` service available.

#### Installation

```ShellSession
$ brew install mosh
```
