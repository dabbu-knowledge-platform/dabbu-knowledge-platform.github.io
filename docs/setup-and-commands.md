---
layout: default
title: Setup and Commands
nav_order: 3
---

## Setup

Once Dabbu is started for the first time, it will ask you for a server URL. There is a server hosted on Heroku (`https://dabbu-server.herokuapp.com`), which is free to use. But it is recommended to setup and run the server on your own machine if you can. Instructions to do that are given [here](https://github.com/dabbu-knowledge-platform/files-api-server/blob/develop/docs/running-the-server.md).

If you decide to use the free server, enter `https://dabbu-server.herokuapp.com` as the server URL. If you decide to set it up on your own machine, enter `http://localhost:<PORT NUMBER>` as the server URL, where `<PORT NUMBER>` is the port the server is running on (printed out when the server starts). To change the server URL later on, use the config command as follows: `config set serverURL <YOUR NEW URL>`.

Then, Dabbu will ask you to setup your first 'drive'. A drive is just like a usb drive attached to your computer - `c:`, `d:`, `e:`, etc - but instead of showing files from the USB drive, it shows you files and folders from a certain provider (Gmail, Google Drive, OneDrive, ...). Follow the instructions Dabbu shows you to setup the drive.

You can use several commands to tell Dabbu what you want to do. Read on to know more about how to use them.

Also, if you run into any problems while installing or using Dabbu CLI, feel free to ask [here](https://github.com/dabbu-knowledge-platform/cli/discussions/categories/q-a). We'll only be glad to help :)

## Using commands

### The prompt

Once a drive is created, you will see something called a 'prompt' on the screen. It looks like this:

```
<drive name>:/$
```

> For those who are already familiar with the bash shell: Dabbu is sort of a shell, and its commands are very similar to bash commands. Take a look at the [summary of CLI commands](#a-brief-summary-of-cli-commands) for a quick summary of all the commands you can run.

The prompt shows you what drive which folder/directory you are currently in. You can also type `pwd` (short form for **P**rint **W**orking **D**irectory) and hit `enter` to know that information.

### Moving around

Dabbu has a notion of the _current working directory_, which refers to what folder/directory you are currently in. A special symbol, `.` (the full stop), is used to refer to the current folder/directory you are in. Another special symbol, `..` (two full stops), is used to refer to the _parent folder/directory_ of the current working directory.

The current path is always shown in the prompt after the drive name:

```
<drive name>:<path to folder you are in>$
```

The topmost folder is always called `/` (forward slash). To change folders, type in `cd <folder to move to>/` (`cd` is short form for **C**hange **D**irectory) and hit `enter`. For example, the following command will move you into the directory `Work`:

```
cd Work/
```

**Note**: The forward slash at the end is required - it tells Dabbu that we are talking about a folder.

Now that you have moved into the folder `Work`, the prompt will change to update your current working directory:

```
<drive name>:/Work$
```

To move back into the root folder (`/`), type in `cd ..` (remember that `.` refers to the current working directory, while `..` refers to the parent directory) and hit `enter`. This should move you to the root folder and also update your prompt to show `/` as the current path.

To switch to another drive, type in the following and hit `enter`:

```
cd <drive name>:
```

Notice the colon at the end - it tells Dabbu that you are talking about a drive.

To create a new drive, simply type in `new-drive` and hit enter.

### Listing files and folders

To list files and folders within the your current working directory, type in `list`. For example, if I am in the `Work` directory, typing in `list` will show you a list of the files and folders within the `Work` directory.

Optionally, you can specify which directory's files and folders to list using `list <directory whose files and folders to list>`. For example, if I am in the root (`/`) directory, I can list files from the `Work` directory by typing `list Work/` and hitting `enter`.

The `list` command prints the number of files in that folder (if there are less than 50 files) and a table of the files and folders. The table has 4 columns: `Name`, `Size`, `Type`,`Last Modified Time` and `Actions`. The file/folder name is coloured blue if it is a folder (it also has the words folder written in brackets next to the name) and magenta if it is a file. The size and last modified time are formatted into human readable formats. The type column shows the type of the file. The actions column contains a link that opens the file in the provider's preferred editor. This means that if you click on a link for a from Google Drive, it will open the Google Drive File Viewer to display the file. Use the `read` command to download and view the file on your computer.

### Downloading and viewing files

To download a file to your computer and open it up, type in `read <path to file>` and hit `enter`. This will download the file temporarily on your computer and open it using the default app to open that file on your computer. The file will be deleted once Dabbu is closed. For example, to download the file `Dabbu Design Document` in the `Work` folder, type in the following and hit `enter`:

```
read "Work/Dabbu Design Document"
```

Notice that the path to the file is surrounded by quotes (`"`). This is only required if the file/folder name contains spaces.

If you want to save the file to your hard drive or to another drive, use the `copy` (copy) command as mentioned below.

### Copying/moving files

To copy a file from one drive to another drive, use the `copy` (short form for **c**o**p**y) command as follows:

```
copy <path to file that you want to copy> <path to destination folder>
```

For example, if I want to copy a file (say, `School Project.docx`) from my `Personal` folder on `g:` (where I have set up a Google Drive account) to the `Work` folder on `c:` (where I have set up my hard drive), I would type the following and hit `enter`:

```
copy "g:/Personal/School Project.docx" c:/Work/
```

Notice two things:

- One, the path to the `School Project.docx` file is surrounded by quotes. This is because the file name contains spaces.
- Two, the path to the `Work` folder ends with a `/`. This is to tell Dabbu that `Work` is a folder.

If I want to copy the file `School Project.docx` from my `Personal` folder on `g:` (where I have set up a Google Drive account) to the `Work` folder on `c:` (where I have set up my hard drive) and rename it to `MyProject.docx`, I would type the following and hit `enter`:

```
copy "g:/Personal/School Project.docx" c:/Work/MyProject.docx
```

Notice two things:

- One, the path to the `School Project.docx` file is surrounded by squotes. This is because the file name contains spaces.
- Two, the path to the destination does not end with a `/`. This i because we are copying the file to another file, and not another folder.

To rename a file without copying it, or to move a file instead of copying it, just use `mv` instead of `copy`.

### Deleting files

To delete a file on a certain drive, use the `del` ((short form for **r**e**m**ove)) command. For example, to delete the file `Dabbu Design Document` in the `Work` folder, type in the following and hit `enter`:

```
del "Work/Dabbu Design Document"
```

Notice that the path to the file is surrounded by quotes (`"`). This is only required if the file/folder name contains spaces.

To delete the entire work folder:

```
del Work/
```

Notice that the path to the `Work` folder ends with a `/`. This is to tell Dabbu that `Work` is a folder.

Be careful while using the `del` command as it usually permanently deletes files and folders.

## A Brief Summary of CLI Commands

**Note:**

- Anything in <> must be mentioned, while if it is in [], it is optional.
- All file/folder paths may include drive names.
- While specifying a folder, please add a / at the end of the folder name.
- Escape spaces in the file name by surrounding it in quotes.

**Commands:**

- `pwd` - Know your current drive and folder
- `cd <drive name>:` - Switch drives (Notice the colon at the end of the drive name)
- `cd <relative path to folder>` - Move into a folder
- `list [relative path to folder]` - List files in a folder (default is current folder)
- `read <relative path to file>` - Download and open a file
- `copy <relative path to file> <relative path to place to copy to>` - Copy a file from one place to another
- `del <relative path to file>` - Delete a file
- `new-drive` - Create a new drive
- `config <get | set | del> <field path> [value to set]` - View/set/delete a field in the config file
- `clear` - Clear the screen
- `CTRL+C OR exit` - Exit

Typing any of the above and then hitting enter will allow you to execute that command and get a result.

# Providers supported

- **Hard drive**
- [**Google drive**](https://github.com/dabbu-knowledge-platform/files-api-server/blob/develop/docs/providers/googledrive.md)
- [**Gmail**](https://github.com/dabbu-knowledge-platform/files-api-server/blob/develop/docs/providers/gmail.md)
- [**One Drive**](https://github.com/dabbu-knowledge-platform/files-api-server/blob/develop/docs/providers/onedrive.md)

To request a new provider, file an issue [here](https://github.com/dabbu-knowledge-platform/files-api-server/issues/new/choose).
