## `Perl`

### Setup `CPAN`

With every user you want perl being setup, run:

```ShellSession
$ cpan
```

and choose the default answer to all questions, except when it asks for adding environment variables to `.zshrc` because:

1. We use `Fizzy` to manage configurations. Those environment variables are [here](https://github.com/alem0lars/configs/blob/master/linux/gentoo/env/90perl.tt)
2. Those environment variables should be *always* available, even for non-interactive / non-`zsh` sessions.
