# Bootable USB Installer

To create a bootable USB-drive containing the `OSX` installer, perform the following steps:

1. If you didn't already do, download the latest version of the `OSX` installer from the `Mac App Store`.
2. Format the USB-pen with FAT filesystem and give it a name (e.g. `Install OSX`).
3. Burn it in a USB-pen by running:

  ```ShellSession
  $ _usb_volume_path="/Volumes/Install OSX" # Substitute with your USB-pen volume path.
  $ sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume "${_usb_volume_path}" --applicationpath /Applications/Install\ OS\ X\ Yosemite.app --nointeraction
  ```
  
Now your USB-pen should be a valid `OSX` installer.

*Gratz!*
