# Vim

You can choose to use VIm standalone (*MacVim*) or a VIm compatible modern alternative called *NeoVim*.

## Installation

For NeoVim:

```ShellSession
$ brew tap neovim/homebrew-neovim
$ brew install --HEAD neovim
$ pip install neovim # To enable Python support inside NeoVim.
```

Or if you prefer MacVim:

```ShellSession
$ brew install macvim --override-system-vim --with-lua
$ brew linkapps macvim
```

## Configuration

The configuration is available [here](https://github.com/alem0lars/configs/tree/master/vim).

It can be managed using [Fizzy](https://github.com/alem0lars/fizzy). If you want to do so:

1. Enable the feature `vim`.
2. Assuming that `${vars_name}` is the name of your variables file and `${inst_name}` is the name of the configuration instance that you want to create/update, run:
```ShellSession
$ fizzy cfg sync
$ fizzy cfg instantiate --vars-name="${vars_name}" --inst-name="${inst_name}"
$ fizzy sys install     --vars-name="${vars_name}" --inst-name="${inst_name}"
```

Otherwise, if you want to manually manage your configuration or you just don't want to use Fizzy, then take a look at the configurations files and adjust them considering the ERB expressions (i.e. ice-cream).
