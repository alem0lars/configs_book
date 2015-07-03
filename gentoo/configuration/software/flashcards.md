# Flashcards

## Installation

```ShellSession
# emerge "app-misc/anki"
```

## Configure folder

```ShellSession
# _flashcards_path="/archive/documents/flashcards"
# mkdir -p "${_flashcards_path}"
# echo "#\!/usr/bin/env sh\n\n/usr/bin/anki -b \"${_flashcards_path}\"\n" > \
  "/usr/local/bin/anki"
# chmod +x "/usr/local/bin/anki"
```
