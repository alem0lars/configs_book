# IntelliJ IDEA

## Installation

```ShellSession
$ brew cask install intellij-idea --appdir=/Applications
```

## Color Scheme

Install the Monokai color scheme:
```ShellSession
$ git clone https://github.com/y3sh/Intellij-Colors-Sublime-Monokai.git # Download.
$ cd Intellij-Colors-Sublime-Monokai && ./buildjar.sh ; cd ..           # Create the Jar.
```

Import the Monokai color scheme into IntelliJ IDEA:
* Go to `IntelliJ` → `File` → `Import Settings` → `Select Jar` and select the created Jar (`SublimeMonoKai.jar`).
* Select `Sublime Monokai` as the theme in `Settings` → `Editor` → `Colors & Fonts`.
