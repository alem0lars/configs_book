# Haskell

## Installation

```ShellSession
$ brew install ghc
$ brew install cabal-install
```

## Cabal

```ShellSession
$ cabal update
```

## Development tools

```ShellSession
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc aeson
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc happy
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc haskell-src-exts
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc haddock
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc ghc-mod
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc stylish-haskell
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc hdevtools
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc hlint
$ cabal install --global --enable-tests --enable-documentation --haddock-all --ghc haskell-docs
```

## Troubleshooting

### Wrong symlinks for ghc

If you get this warning:

```
Warning: You have unlinked kegs in your Cellar
Leaving kegs unlinked can lead to build-trouble and cause brews that depend on
those kegs to fail to run properly once built. Run `brew link` on these:

    ghc
```

to fix the symlinks you should run:

```ShellSession
$ brew link --overwrite ghc
```
