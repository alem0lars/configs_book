# Unity3d

## Unity Web Player

### Installation

```ShellSession
$ brew cask install unity-web-player
```

## Unity Development Tool

### Installation

Unity doesn't work on case-sensitive filesystems by default.
Since we *still* want a case-sensitive filesystem, since it's more modern, correct, UNIX-style,
we need to:

1. Create a case-insensitive volume and install Unity inside.
2. Link the `Steam.app` into `/Applications`.

We will call the volume `unity`.

#### Step 1

1. In Disk Utility, create a New Image.
3. Choose the location to save the image file.
4. Then, set the image characteristics as below:
  * **Name**: `steam`
  * **Size**: any (the image will expand the size when required and the size is the maximum size the image can take; I suggest `16GB` or more)
  * **Format**: `Mac OS Extended (Jornaled)`
  * **Encryption**: `none`
  * **Partitions**: `No partition map`
  * **Image Format**: `sparse bundle disk image`
5. Mount the image file if it’s not yet mounted.
6. Download the `Unity.pkg` installer and run it. When the installer asks for a location, choose the mounted `unity` volume.

Now everything is stored and confined inside the `unity` volume.

#### Step 2

Create a link for `Steam.app` into `/Applications`: 

```ShellSession
$ ln -s "/Volumes/unity/Applications/Unity/Unity.app" "/Applications"
```

#### (Optional) Setup the Projects directory

Not only the Unity application but also the projects should be stored in a case-insensitive filesystem,
otherwise Unity will just crash.

I didn't find anything better than storing them inside `/Volumes/unity/Projects`.
Of course, you should create that directory:
```ShellSession
$ mkdir /Volumes/unity/Projects
```
