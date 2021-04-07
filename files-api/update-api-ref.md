---
layout: home
title: Update API Specification
nav_order: 9
parent: Dabbu Files API Specification
grand_parent: API Reference
---

# Updating a file's metadata and/or contents

**PUT** : `/data/:providerId/:folderPath/:fileName`

- Request parameters: [Compulsory]

  - `providerId`: Provider ID - `string`
  - `folderPath`: Path to folder - `string`
  - `fileName`: Name of the file - `string`

- Request body: [Posted as multipart form data]

  - The request body may contain any fields that the provider requires to execute the request
  - `content`: The file content - `file-data` [Optional]
  - `name`: The name of the file - `string` [Optional]
  - `path`: The path to the folder in which the file resides - `string` [Optional]
  - `createdAtTime`: Time the file was created (may not be supported by all providers) - `timestamp` [Optional]
  - `lastModifiedTime`: Last time the file's content or metadata (varies from provider to provider) was changed (may not be supported by all providers) - `timestamp` [Optional]

- Response:

  - `code`: The HTTP response code (200 if successful) - `number`
  - `error`: Object containing `message` and `reason` fields - `object`
  - `content`: The [files resource](/schema/files-resource.schema.json) that was just updated - `file`

- Errors:
  - `404`: The file was not found - `notFound`
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`
  - `501`: Provider not available - `providerNotFound`
