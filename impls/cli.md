---
layout: home
title: Dabbu CLI
nav_order: 14
parent: Clients and API Implementations
---

# Dabbu CLI

Dabbu CLI (command line interface) allows you to access files and folders from your hard drive, Google Drive, MS One Drive and Gmail - all from one place. A web interface is a work in progress.

## Installation

To install the CLI on your computer, you can simply download the latest version of it [here](https://github.com/dabbu-knowledge-platform/dabbu-cli/releases/latest).

## Running the CLI

On Windows, simply double click the file to run it (it will be a `.exe`).

On Linux/MacOS, mark the file as an executable by running `chmod u+x path/to/file`. Then simply type in the path to the file in Terminal.

Once the CLI is started for the first time, it will ask you for a server URL. There is a public instance of the server running on [Heroku](https://dabbu-server.herokuapp.com/), but it is recommended (and very easy) to download it to your computer and run it. To setup a server on your own computer, simply follow the instructions given [here](./server).

If you run into any problems while installing or using the CLI, feel free to ask [here](https://github.com/dabbu-knowledge-platform/cli/discussions/categories/q-a). We'll only be glad to help :)

## Using the CLI

Upon starting the CLI for the first time, it will present you with a setup flow. It will ask you to enter the server URL (which is http://localhost:8080 if you are running the server on your computer) and then to setup a 'drive'. 

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
- `<drive name>:` - Switch drives (Notice the colon at the end of the drive name)
- `::` - Create a new drive
- `clear` - Clear the screen
- `CTRL+C` - Exit

Typing any of the above and then hitting enter will allow you to execute that command and get a result.

If you run into any problems while installing or using the CLI, feel free to ask [here](https://github.com/dabbu-knowledge-platform/cli/discussions/categories/q-a). We'll only be glad to help :)