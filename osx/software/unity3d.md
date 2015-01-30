# Unity3d

## Unity development environment

### Installation

Unity doesn't work on case-sensitive filesystems by default.
Since we *still* want a case-sensitive filesystem, since it's more modern, correct, UNIX-style,
we need to:

1. Create a case-insensitive volume and install Unity inside.
2. Link the `Unity.app` into `/Applications`.

We will call the volume `Unity`.

#### Step 1

1. In Disk Utility, create a New Image.
3. Choose the location to save the image file.
4. Then, set the image characteristics as below:
  * **Name**: `Unity`
  * **Size**: any (the image will expand the size when required and the size is the maximum size the image can take; I suggest `16GB` or more)
  * **Format**: `Mac OS Extended (Jornaled)`
  * **Encryption**: `none`
  * **Partitions**: `No partition map`
  * **Image Format**: `sparse bundle disk image`
5. Mount the image file if it’s not yet mounted.
6. Download the `Unity.pkg` installer and run it. When the installer asks for a location, choose the mounted `Unity` volume.

Now everything is stored and confined inside the `Unity` volume.

#### Step 2

Create a link for `Unity.app` into `/Applications`: 

```ShellSession
$ ln -s "/Volumes/unity/Applications/Unity/Unity.app" "/Applications"
```

#### (Optional) Setup the Projects directory

Not only the Unity application but also the projects should be stored in a case-insensitive filesystem, otherwise Unity will just crash.

There are some options available:

* The simplest is to create a directory inside the unity volume:

  ```ShellSession
  $ mkdir /Volumes/Unity/Projects
  ```

* If you don't like the option above (*like me*), another option is to create a dedicated volume for unity project (e.g. a volume called `Unity Workspace` stored in `~/Develop/Workspaces`).

## Unity Web Player

### Installation

```ShellSession
$ brew cask install unity-web-player
```
