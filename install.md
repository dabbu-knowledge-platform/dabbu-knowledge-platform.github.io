---
layout: default
title: Installation
nav_order: 2
---

# Installation

Excited to use Dabbu? Here's how to install it on your machine:

## Windows

Download the latest `windows-generic` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, unzip it and run the `.exe` file by double clicking on it. Run the `.exe` file every time you want to run the CLI.

[Setup and Commands \>\>](./setup-and-commands)

## MacOS

Download the latest `macos-pkg` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, simply double click on the .pkg file to install the CLI. Then run the CLI from the terminal by typing `dabbu-cli` and hitting enter.

If this method does not work, download the latest `macos-generic` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, unzip and extract all the files into a directory (for example, ~/Downloads/dabbu-cli-macos-generic-amd64/). Then run the following in terminal:

```bash
cp ~/Downloads/dabbu-cli-macos-generic-amd64/dabbu-cli /usr/bin/
chmod 777 /usr/bin/dabbu-cli
```

Then run the CLI by typing `dabbu-cli` and hitting enter.

[Setup and Commands \>\>](./setup-and-commands)

## Linux - DEB file (Debian/Ubuntu/Linux Mint/etc)

Download the latest `linux-deb` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, simply double click on the `.deb` file to install the CLI. Then run the CLI from the terminal by typing `dabbu-cli` and hitting enter.

If double clicking the `.deb` file does not open it in software centre, run the following in terminal (this command assumes you downloaded the `.deb` file to `~/Downloads/dabbu-cli-linux-deb-amd64.deb`):

```bash
dpkg -i ~/Downloads/dabbu-cli-linux-deb-amd64.deb
```

Then run the CLI from the terminal by typing `dabbu-cli` and hitting enter.

[Setup and Commands \>\>](./setup-and-commands)

## Linux - RPM file (RedHat/CentOS/Fedora/etc)

Download the latest `linux-rpm` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, simply double click on the `.rpm` file to install the CLI. Then run the CLI from the terminal by typing `dabbu-cli` and hitting enter.

If double clicking the `.rpm` file does not open it in software centre, run the following in terminal (this command assumes you downloaded the `.rpm` file to `~/Downloads/dabbu-cli-linux-rpm-amd64.rpm`):

```bash
rpm -ivh ~/Downloads/dabbu-cli-linux-rpm-amd64.rpm
```

Then run the CLI from the terminal by typing `dabbu-cli` and hitting enter.

[Setup and Commands \>\>](./setup-and-commands)

## Linux - Arch Linux/Manjaro

Download the latest `linux-arch` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, run the following in terminal (this command assumes you downloaded the `.tar.gz` file to `~/Downloads/dabbu-cli-linux-arch-amd64.tar.gz`):

```bash
pacman -U ~/Downloads/dabbu-cli-linux-arch-amd64.tar.gz
```

Then run the CLI from the terminal by typing `dabbu-cli` and hitting enter.

[Setup and Commands \>\>](./setup-and-commands)

## Linux - Alpine

Download the latest `linux-alpine` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, run the following in terminal (this command assumes you downloaded the `.apk` file to `~/Downloads/dabbu-cli-linux-alpine-amd64.apk`):

```bash
apk add --allow-untrusted ~/Downloads/dabbu-cli-linux-alpine-amd64.apk
```

> Note: The --allow-untrusted flag is required as we do not sign the file as of now. If you do not feel comfortable using this flag, skip to [building the CLI from source](#building-from-source-macos-and-linux-only).

Then run the CLI by typing `dabbu-cli` and hitting enter.

[Setup and Commands \>\>](./setup-and-commands)

## Linux - Generic

If you want to install the executable yourself, download the latest `linux-generic` release from the [releases page](https://github.com/dabbu-knowledge-platform/cli/releases/latest). Once downloaded, unzip and extract all the files into a directory (for example, ~/Downloads/dabbu-cli-linux-generic-amd64/). Then run the following in terminal:

```bash
cp ~/Downloads/dabbu-cli-linux-generic-amd64/dabbu-cli /usr/bin/
chmod 777 /usr/bin/dabbu-cli
# The following commands are optional, but recommended
cp ~/Downloads/dabbu-cli-linux-generic-amd64/dabbu-cli.1 /usr/share/man/man1/
cp ~/Downloads/dabbu-cli-linux-generic-amd64/logo.png /usr/share/icons/dabbu-cli.png
cp ~/Downloads/dabbu-cli-linux-generic-amd64/dabbu-cli.desktop /usr/share/applications/
```

Then run the CLI by typing `dabbu-cli` and hitting enter.

If you run into any problems while installing or using Dabbu CLI, feel free to ask [here](https://github.com/dabbu-knowledge-platform/cli/discussions/categories/q-a). We'll only be glad to help :)

[Setup and Commands \>\>](./setup-and-commands)

## Building from source (MacOS and Linux only)

To build the CLI from source, follow the instructions given below:

### Install `git`, `nodejs` and `yarn`.

`git` **must** be installed to download the source code. If you do not want to install `git`, download the source code from [here](https://github.com/dabbu-knowledge-platform/cli/archive/refs/heads/stable.zip) and unzip it instead.

- To check if git is already installed, type `git --version` in terminal/command prompt. You should see a version number displayed after running this command.
- [Here](https://github.com/git-guides/install-git) are the official instructions to install git for all platforms in case you haven't installed it already.

`nodejs` and `yarn` **must** be installed to run the CLI locally.

- To check if NodeJS and Yarn already installed, type `node --version && yarn --version` in terminal/command prompt. You should see two version numbers displayed after running this command. For developing Dabbu CLI, we use the latest version of Typescript, which compiles to CommonJS code.
- [Here](https://nodejs.org/en/download/package-manager/) are the official instructions to install NodeJS and Yarn for all platforms in case you haven't installed it already.

### Clone the source code

Run the following in a terminal to clone the repository locally:

```sh
$ git clone https://github.com/dabbu-knowledge-platform/cli
$ cd cli
$ git checkout stable # replace stable with develop for the latest beta version
```

If you have downloaded the source code instead, unzip it:

```sh
$ unzip ~/Downloads/cli-stable.zip
$ cd cli-stable
```

### Build the CLI

To build the CLI, run the following command:

```sh
$ yarn
$ yarn package
```

If the command runs successfully, you will be able to see the generated packages in the `dist/packages/` folder and binaries in the `dist/binaries/` folder. The packages are the same as the ones distributed as part of the [latest release](https://github.com/dabbu-knowledge-platform/cli/releases/latest/). The binaries generated (`cli-alpine`, `cli-linux`, `cli-macos`, and `cli-win.exe`) can be run on alpine, linux, macos and windows respectively without installation of external dependencies.

On Windows, you can double click on the `.exe` file from file manager to run the CLI. On Linux/MacOS, simply type the path to the files (`./dist/cli-alpine` OR `./dist/cli-linux` OR `./dist/cli-macos`) in terminal and hit enter to run the CLI.

[Setup and Commands \>\>](./setup-and-commands)
