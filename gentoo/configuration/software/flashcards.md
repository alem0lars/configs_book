# Flashcards

## Installation

```ShellSession
# emerge "app-misc/anki"
```

## Configure folder

```ShellSession
# mkdir -p "/data/documents/flashcards" # Replace with your flashcards directory path
# echo "#\!/usr/bin/env sh\n\n/usr/bin/anki -b \"${_flashcards_path}\"\n" > \
  "/usr/local/bin/anki"
# chmod +x "/usr/local/bin/anki"
```
