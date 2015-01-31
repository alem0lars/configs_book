# Unity3d

## Unity development environment

### Installation

Unity doesn't work on case-sensitive filesystems by default.
Since we *still* want a case-sensitive filesystem, since it's more modern, correct, UNIX-style,
we need to:

1. Create a case-insensitive volume and install Unity inside.
2. Link the `Unity.app` into `/Applications`.
3. Setup links to the current user's library.

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
$ ln -s "/Volumes/Unity/Applications/Unity/Unity.app" "/Applications"
```

#### Step 3

When you open MonoDevelop-Unity with your current user, it will create some Library files and folders.

It's a good practice that you also keep those files inside the volume, so you will need to:

1. Create the `Application Support` directory inside the volume.

   ```ShellSession
   $ mkdir -p "/Volumes/Unity/Library/Application Support"
   ```

2. Create the directories:

   ```ShellSession
   $ mkdir -p "/Volumes/Unity/Library/MonoDevelop-Unity-4.0"
   $ mkdir -p "/Volumes/Unity/Library/Application Support/MonoDevelop-Unity-4.0"
   ```

3. Create links to the created directories:

   ```ShellSession
   $ ln -s "/Volumes/Unity/Library/MonoDevelop-Unity-4.0" "${HOME}/Library/MonoDevelop-Unity-4.0"
   $ ln -s "/Volumes/Unity/Library/Application Support/MonoDevelop-Unity-4.0" "${HOME}/Library/Application Support/MonoDevelop-Unity-4.0"
   ```
   
Now you can start MonoDevelop without any troubles :)

#### (Optional) Setup the Projects directory

Not only the Unity application but also the projects should be stored in a case-insensitive filesystem, otherwise Unity will just crash.

There are some options available:

* The simplest is to create a directory inside the unity volume:

  ```ShellSession
  $ mkdir "/Volumes/Unity/Projects"
  ```

* If you don't like the option above (*like me*), another option is to create a dedicated volume for unity project (e.g. a volume called `Unity Workspace` stored in `~/Develop/Workspaces`).

## Unity Web Player

### Installation

```ShellSession
$ brew cask install unity-web-player
```
