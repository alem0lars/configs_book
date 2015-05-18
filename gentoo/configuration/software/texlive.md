# `TeXlive`

## Installation

```ShellSession
$ emerge dev-tex/texmfind # Contains a program to search for the Gentoo package containing a tex package.
$ emerge app-eselect/eselect-pdftex
$ emerge texlive
```

## Configuration

List available distributions with the following command:

```ShellSession
$ eselect pdftex list
```

Set the distribution:

```ShellSession
$ eselect pdftex set 1
```

## Troubleshooting

### Update `TeXlive`

Run:

```ShellSession
$ texmf-update
```
