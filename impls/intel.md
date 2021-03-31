---
layout: home
title: Dabbu Intel API Server
nav_order: 14
parent: Clients and API Implementations
---

# Dabbu Intel API Server
{: .d-inline-block }

Beta
{: .label .label-blue }

The Dabbu Intel API Server can extract topics, people and places from various files (docx, pptx, xlsx, pdf and plain text content) and summarize the content in files regarding a certain topic. It is an implementation of the Dabbu Intel API.

The Intel API Server is currently in **development stage**. Current features include:

- extraction of topics, people and places from various files (docx, pptx, xlsx, pdf and plain text content)

Upcoming features include:

- summarization of the content in files regarding a certain topic

## Installation

To install the server on your computer, you can simply download the latest version of it [here](https://github.com/dabbu-knowledge-platform/intel-api-server/releases/latest).

## Running the server

> **Note**: It is **recommended** that you move the executable to a separate folder (the servers and CLI can be put in the same folder) and run it from there. This is because the server will create a folder `_dabbu` which contains several important files. When moving the executable anywhere else, make sure you move the `_dabbu` folder as well.

On Windows, simply double click the file to run it (it will be a `.exe`).

On Linux/MacOS, mark the file as an executable by running `chmod u+x path/to/file`. Then simply type in the path to the file in Terminal.

Always ensure the server is running before starting an application that uses it.

If you run into any problems while installing or using the server, feel free to ask [here](https://github.com/dabbu-knowledge-platform/intel-api-server/discussions/categories/q-a). We'll only be glad to help :)

## Applications that use the Dabbu Intel API

- [Dabbu CLI](./cli)

## Code examples for HTTP requests

> To view the API specification (required URL params, headers, request body fields, etc), go [here](../intel_api/index).
