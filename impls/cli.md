---
layout: home
title: Dabbu CLI
nav_order: 15
parent: Clients and API Implementations
---

# Dabbu CLI

Dabbu CLI (command line interface) allows you to access files and folders from your hard drive, Google Drive, MS One Drive and Gmail - all from one place. A web interface is a work in progress.

## Installation

### Linux/MacOS

On Linux/MacOS, simply type the following in your terminal and follow on-screen instructions:

```
$ wget https://raw.githubusercontent.com/dabbu-knowledge-platform/cli/main/scripts/install -O - | bash
```
<sub>Hint: No need to copy the $ sign at the beginning</sub>

Then type `dabbu-cli` to run the CLI.

#### Advanced options

To simply do a dry run, save the install script and then run it with the -f option:

```
$ wget https://raw.githubusercontent.com/dabbu-knowledge-platform/cli/main/scripts/install
$ ./install -f
```

To reinstall the script, run the script with the -o option:

```
$ wget https://raw.githubusercontent.com/dabbu-knowledge-platform/cli/main/scripts/install
$ ./install -o
```

### Windows

<sub>An installer script for windows is in progress</sub>

To install the CLI on your computer, you can simply download the latest version of it [here](https://github.com/dabbu-knowledge-platform/dabbu-cli/releases/latest).

> **Note (for Windows)**: It is **recommended** that you move the executable to a separate folder (the servers and CLI can be put in the same folder) and run it from there. This is because the CLI will create a folder `_dabbu` which contains several important files. When moving the executable anywhere else, make sure you move the `_dabbu` folder as well.

Once download, simply double click the file to run it (it will be a `.exe`).

Once the CLI is started for the first time, it will ask you for a server URL. There is a public instance of the server running on [Heroku](https://dabbu-server.herokuapp.com/), but it is recommended (and very easy) to download it to your computer and run it. To setup a server on your own computer, simply follow the instructions given [here](/impls/server). Always start the server before using the CLI. (URL if the server is running on your computer - http://localhost:8080)

If you run into any problems while installing or using the CLI, feel free to ask [here](https://github.com/dabbu-knowledge-platform/cli/discussions/categories/q-a). We'll only be glad to help :)

## Setting up

A drive, just like physical drives on your computer - `c:`, `d:`, `e:`, etc., allows you to access files and folders from a certain provider. Follow the instructions the CLI shows you to setup the drive.

Once the drive is setup, it will display a prompt that looks like this:

```
<drive_name>:$ 
```

You can use several commands to tell the CLI what you want to do. Here is a brief summary of all of them:

**Remember:**

- Anything in <> must be mentioned, while if it is in [], it is optional.
- All file/folder paths may include drive names.
- While specifying a folder, please add a / at the end of the folder name.
- Escape spaces in the file name by surrounding it in quotes.

**Commands:**

- `pwd` - Know your current drive and folder
- `cd <relative path to folder>` - Move into a folder
- `ls [relative path to folder]` - List files in a folder (default is current folder)
- `cat <relative path to file>` - Download and open a file
- `cp <relative path to file> <relative path to place to copy to>` - Copy a file from one place to another
- `mv <relative path to file> <relative path to place to copy to>` - Move a file from one place to another
- `rm <relative path to file>` - Delete a file
- `sync <relative path to folder> <relative path to folder to sync files to>` - Sync files from one folder to another efficiently
- `<drive name>:` - Switch drives (Notice the colon at the end of the drive name)
- `::` - Create a new drive
- `clear` - Clear the screen
- `CTRL+C` - Exit

Typing any of the above and then hitting enter will allow you to execute that command and get a result.

If you run into any problems while installing or using the CLI, feel free to ask [here](https://github.com/dabbu-knowledge-platform/cli/discussions/categories/q-a). We'll only be glad to help :)

### Knowledge Drive

The latest version of Dabbu CLI also supports a special `knowledge` drive. This drive will, on startup, **'index'** all your files - it will extract topics, people and places from the file's content. It will then treat these as folders, that you can move into and view which files are related to which topic.

To setup the `knowledge` drive, simply type in `::` into the Dabbu CLI command prompt and choose `knowledge` as the provider. Follow the instructions on screen to select which drives' files you wish to index. Once the indexing process is over, you may list out the files related to a certain topic/person/place and view the files too.

If any files have changed, you will have to recreate the drive to see the changes. This is being fixed (refer to issue [cli#21](https://github.com/dabbu-knowledge-platform/cli/issues/21) on Github).
