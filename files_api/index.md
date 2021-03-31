---
layout: home
title: Dabbu Files API Specification
nav_order: 5
parent: Architecture and Specifications
has_children: true
---

# Dabbu Files API Specification

Dabbu Files API is a REST API to interact with your files and folders from multiple providers and get them in a single, unified format. You can access these APIs using **simple HTTP requests.**

## Resources in Dabbu

In Dabbu, all resources are either files or folders. These resources are represented as **JSON objects** as defined [here](/schema/files_resource.schema.json).

## Authorization for certain providers

Some providers require authorization from the user to access the resources stored with them, while others don't. For example, Google Drive, One Drive and Gmail require OAuth2 authorization, while the Hard Drive provider does not need any authorization.

Currently, if a provider needs authorization, **the client application is responsible** to gain user consent to access their Google Drive/One Drive/Gmail and obtain an access token and refresh token from the provider. Once the client application gains an access token from the respective provider, they can pass the access token to the server in the 'Authorization' header.

The provider on the server will use this access token to perform the specified operation on the user's files in that drive.

Details of a method to handle this authorization process are given [here](./client_config).

## Things to keep in mind while making HTTP requests

Always ensure that all folder paths are **delimited with a forward slash** and not a back slash.

Always ensure that the provider ID, folder path, file name and query parameters are **URL encoded**.

Always ensure you have **supplied required fields in the request body and request headers** for that particular provider. For example, the Hard Drive requires a field in the request body called `base_path`, containing the path to the folder to treat as root while retrieving a resource. For details on what provider requires what fields/headers, take a look at [this](./client_config).

## Supported HTTP methods

There are several actions you can perform on resources by making HTTP requests to the API. Dabbu allows you to perform the following actions:

- list files and folders in a folder of a provider [GET]
- get information about a particular file at a certain path [GET]
- create a file at a certain path [POST]
- update the metadata and/or contents of a file at a certain path [PUT]
- delete a file or folder at a certain path [DELETE]
