# MacTeX

## Installation

```ShellSession
$ brew cask install mactex --appdir=/Applications
$ luaotfload-tool --update # Genereate the font names database.
```

## Packages

Update all packages:

1. Open `TeX Live Utility`
2. Click `Actions ‣ Refresh Package List`
3. Click `Actions ‣ Update All Packages`

## Configuration

### TeX Live Utility

* Enable `Automatically enable fonts in my home directory`

### BibDesk

* Set `TeX Preview ‣ TeX template encoding` to `Unicode (UTF-8)`
* Enable `Sharing ‣ Look for shared bibliographies`

### LaTeXiT

* Set `TeX Editing ‣ Appearance ‣ Default Font` to `Menlo Regular 11.0`
* Select `Typesetting ‣ Behaviour ‣ xelatex`
* Enable `History ‣ Smart history`
* Enable `Web ‣ Check for updates on launch`

### TeXShop

* Set `Source ‣ Document Font` to `Menlo Regular 11.0`
* Set `Source ‣ Editor ‣ Tab` to `2`
* Set `Source ‣ Encoding` to `Unicode (UTF-8)`
* Select `Source ‣ Command Completion Triggered By ‣ Tab Key`
* Enable `Preview ‣ External Editor ‣ Automatic Preview Update`
* Set `Console ‣ Console Font` to `Menlo Regular 11.0`
* Set `Typesetting ‣ Default Command` to `XeLaTeX`
* Enable `Typesetting ‣ During File Save ‣ Save related files`

## Troubleshooting

### Font missing error

If you have installed a font but the LaTeX compiler says that font is still missing, maybe you need to update the font names database, running:

```ShellSession
$ luaotfload-tool --update
```
