# QuickLook

## Extensions

```ShellSession
$ brew cask install qlcolorcode        --appdir=/Applications
$ brew cask install qlstephen          --appdir=/Applications
$ brew cask install qlmarkdown         --appdir=/Applications
$ brew cask install quicklook-json     --appdir=/Applications
$ brew cask install qlprettypatch      --appdir=/Applications
$ brew cask install quicklook-csv      --appdir=/Applications
$ brew cask install betterzipql        --appdir=/Applications
$ brew cask install webp-quicklook     --appdir=/Applications
$ brew cask install suspicious-package --appdir=/Applications
$ brew cask install provisionql        --appdir=/Applications
$ brew cask install cert-quicklook     --appdir=/Applications
```

## Configuration

* Enable the text selection in QuickLook:

  ```ShellSession
  $ defaults write com.apple.finder QLEnableTextSelection -bool true && killall Finder
  ```

