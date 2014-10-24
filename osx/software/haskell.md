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
```
