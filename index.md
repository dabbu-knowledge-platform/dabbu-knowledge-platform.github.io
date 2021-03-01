---
layout: home
title: Overview
nav_order: 1
---

# Overview

With the Dabbu Knowledge Platform, we aim to rethink the way we organize and traverse large amounts of knowledge, no matter where it is stored.

## Current feature set

The currently implemented features include:

- Abstract access to information/data stored with multiple providers (Hard drive, Google Drive, One Drive, Gmail).
- Conversion of proprietory formats to open formats or markdown.

## Planned features

The following is a list of features that are planned or in progress:

- Extraction of topics, people and places from knowledge stored with multiple providers.
- One pagers/summaries regarding all knowledge around a certain topic, person or place based on information/data from multiple providers.
- Navigation by topic, person or place in a knowledge graph.
- Syncing information/data from one provider to another.

## Getting started

Excited to use Dabbu? Here's how to get started:

### Dabbu CLI

There currently exists a CLI (command line interface) that allows you to access files and folders from your hard drive, Google Drive, MS One Drive and Gmail - all from one place. A web interface is still in progress.

The CLI requires Dabbu Files API Server to be running locally or remotely (you just need to know the server URL) to interact with your files.

To get started with the CLI, take a look at the instructions [here](./impls/cli).

### Dabbu Files API Server

Dabbu Files API Server allows apps abstract access to the user's information stored with multiple providers.

To view instructions to install the server, go [here](./impls/server).

## Architecture

To know more about how the Dabbu Knowledge Platform is designed and how it works, take a look [here](./architecture/).
