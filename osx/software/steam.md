# Steam

## Installation

Since Steam works only in case-insensitive filesystems, to install steam in a case-sensitive filesystem you should:
1. Create a case-insensitive volume and install Steam inside.
2. Where Steam access files, make links to point inside the volume.

We will call the volume `steam`.

### Step 1

1. In Disk Utility, create a New Image.
3. Choose the location to save the image file.
4. Then, set the image characteristics as below:
  * **Name**: `steam`
  * **Size**: any (the image will expand the size when required and the size is the maximum size the image can take; I suggest `32GB` or more)
  * **Format**: `Mac OS Extended (Jornaled)`
  * **Encryption**: `none`
  * **Partitions**: `No partition map`
  * **Image Format**: `sparse bundle disk image`
5. Mount the image file if it’s not yet mounted.
6. Download and copy the Steam app for Mac into the mounted image.

### Step 2

Create the real directories where Steam should point to:
```ShellSession
$ mkdir -p "/Volumes/steam/Application Support/Steam"
$ mkdir -p "/Volumes/steam/Steam Content"
```

Make the links:
```ShellSession
$ ln -s "/Volumes/steam/Application Support/Steam" "~/Library/Application Support/Steam"
$ ln -s "/Volumes/steam/Steam Content" "~/Documents/Steam Content"
$ ln -s "/Volumes/steam/Steam.app" "/Applications" # Create a link to the app inside /Applications
```
