# Archive configuration

If you have a separate partition for your documents, projects, music, videos, etc.. like me (I call it archive), then you should setup it.

*You should already have it mounted in `/archive` and an entry in `/etc/fstab`.*

## Structure

The basic directory structure is the following:

```
/archive
  → documents
  → graphics
    → images
  → audio
    → music
  → video
    → movies
  → development
    → projects
      → personal
      → work
      → contrib
    → workspaces
```

## Setup

To create those directories run:

* Documents:

  ```ShellSession
  $ mkdir -p /archive/documents

  $ groupadd archive_documents                         # Create a new group.
  $ chown -R root:archive_documents /archive/documents # Set the group.
  $ usermod -a -G archive_documents alem0lars          # (Optional) Add your user to the group.

  $ chmod -R 770 /archive/documents                           # Change permissions for existing directories.
  $ setfacl -d -R -m u::7 /archive/documents                  # Set default user permissions to `rwx` for directories.
  $ setfacl -d -R -m g:archive_documents:7 /archive/documents # Set default group permissions to `rwx` for directories.
  $ setfacl -d -R -m o::0 /archive/documents                  # Disallow access for other users.
  ```

* Graphics:

  ```ShellSession
  $ mkdir -p /archive/graphics/images

  $ groupadd archive_graphics                        # Create a new group.
  $ chown -R root:archive_graphics /archive/graphics # Set the group.
  $ usermod -a -G archive_graphics alem0lars         # (Optional) Add your user to the group.

  $ chmod -R 770 /archive/graphics                          # Change permissions for existing directories.
  $ setfacl -d -R -m u::7 /archive/graphics                 # Set default user permissions to `rwx` for directories.
  $ setfacl -d -R -m g:archive_graphics:7 /archive/graphics # Set default group permissions to `rwx` for directories.
  $ setfacl -d -R -m o::0 /archive/graphics                 # Disallow access for other users.
  ```

* Audio:

  ```ShellSession
  $ mkdir -p /archive/audio/music

  $ groupadd archive_audio                     # Create a new group.
  $ chown -R root:archive_audio /archive/audio # Set the group.
  $ usermod -a -G archive_audio alem0lars      # (Optional) Add your user to the group.

  $ chmod -R 770 /archive/audio                       # Change permissions for existing directories.
  $ setfacl -d -R -m u::7 /archive/audio              # Set default user permissions to `rwx` for directories.
  $ setfacl -d -R -m g:archive_audio:7 /archive/audio # Set default group permissions to `rwx` for directories.
  $ setfacl -d -R -m o::0 /archive/audio              # Disallow access for other users.
  ```
  
* Video:

  ```ShellSession
  $ mkdir -p /archive/video/movies

  $ groupadd archive_video                     # Create a new group.
  $ chown -R root:archive_video /archive/video # Set the group.
  $ usermod -a -G archive_video alem0lars      # (Optional) Add your user to the group.

  $ chmod -R 770 /archive/video                       # Change permissions for existing directories.
  $ setfacl -d -R -m u::7 /archive/video              # Set default user permissions to `rwx` for directories.
  $ setfacl -d -R -m g:archive_video:7 /archive/video # Set default group permissions to `rwx` for directories.
  $ setfacl -d -R -m o::0 /archive/video              # Disallow access for other users.
  ```

* Development:

  ```ShellSession
  $ mkdir -p /archive/development/{workspaces,projects/{personal,work,contrib}}

  $ groupadd archive_development                           # Create a new group.
  $ chown -R root:archive_development /archive/development # Set the group.
  $ usermod -a -G archive_development alem0lars            # (Optional) Add your user to the group.

  $ chmod -R 770 /archive/development                             # Change permissions for existing directories.
  $ setfacl -d -R -m u::7 /archive/development                    # Set default user permissions to `rwx` for directories.
  $ setfacl -d -R -m g:archive_development:7 /archive/development # Set default group permissions to `rwx` for directories.
  $ setfacl -d -R -m o::0 /archive/development                    # Disallow access for other users.
  ```
