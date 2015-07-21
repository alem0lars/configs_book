# Dict

## Google Translate

### Installation

```ShellSession
# emerge "app-text/translate-shell"
```

## `Aspell`

`Aspell` is the *spell-checking* solution of choice.
You can use it to check correct / wrong words.

## Installation

```ShellSession
# emerge "app-text/aspell"
```

## Dictionaries

### Installation

```ShellSession
# _langs=(en it) # Replace with languages you want to spell-check.
# for _lang in "${_langs[@]}"; do emerge "app-dicts/aspell-${_lang}"; done
```
