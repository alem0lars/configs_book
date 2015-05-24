# Dict

## `Aspell`

`Aspell` is the *spell-checking* solution of choice.
You can use it to check correct / wrong words.

## Installation

```ShellSession
$ emerge aspell
```

## Dictionaries

### Installation

```ShellSession
$ _langs=(en it) # Replace with languages you want to spell-check.
$ for _lang in "${_langs[@]}"; do echo "aspell-${_lang}"; done
```