---
layout: home
title: Delete API Specification
nav_order: 10
parent: Dabbu Files API Specification
grand_parent: Architecture and Specifications
---

# Deleting a file or folder

**DELETE** : `/data/:providerId/:folderPath/:fileName?`

- Request parameters: [Compulsory]

  - `providerId`: Provider ID - `string`
  - `folderPath`: Path to folder (If only folder path is given, then the entire folder with its contents will be deleted) - `string`
  - `fileName`: Name of the file - `string` [Optional]

- Request body: [Optional]

  - The request body may contain any fields that the provider requires to execute the request

- Response:

  - `code`: The HTTP response code (204 if successful) - `number`
  - `error`: Object containing `message` and `reason` fields - `object`

- Errors:
  - `404`: The file was not found - `notFound`
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`
  - `501`: Provider not available - `providerNotFound`
