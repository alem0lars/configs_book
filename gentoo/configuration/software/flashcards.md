# Flashcards

## Installation

```ShellSession
# emerge "app-misc/anki"
```

## Configure folder

```ShellSession
# _flashcards_path="/data/documents/flashcards" # Replace with your flashcards directory path
# mkdir -p "${_flashcards_path}"
# echo "#\!/usr/bin/env sh\n\n/usr/bin/anki -b \"${_flashcards_path}\"\n" > \
  "/usr/local/bin/anki"
# chmod +x "/usr/local/bin/anki"
```
