# D

## Installation

You need to have `dlang` overlay enabled.

If you use `Fizzy` and [my configs](https://github.com/alem0lars/configs)
you just need to enable the `dlang` use-flag.

```ShellSession
# emerge "dev-lang/dmd"
# emerge "dev-util/dub"
```

### Notes

If emerging fails because of the PIC feature enabled (mostly found in hardened
profiles), you may need to temporarly change the GCC profile to not-hardened
with `gcc-config`. After emerging, you can restore the hardened profile you had.
