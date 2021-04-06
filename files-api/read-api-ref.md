---
layout: home
title: Get API Specification
nav_order: 7
parent: Dabbu Files API Specification
grand_parent: Architecture and Specifications
---

# Retrieving a file's data

**GET** : `/data/:providerId/:folderPath/:fileName`

- Request parameters: [Compulsory]

  - `providerId`: Provider ID - `string`
  - `folderPath`: Path to folder - `string`
  - `fileName`: Name of the file - `string`

- Query parameters: [Optional]

  - `exportType`: Type of URI that the content should be returned in; `view` for opening it in the provider's editor, `media` for a download link, other values may be accepted by the provider - `string`

- Request body: [Optional]

  - The request body may contain any fields that the provider requires to execute the request

- Response:

  - `code`: The HTTP response code (200 if successful) - `number`
  - `error`: Object containing `message` and `reason` fields - `object`
  - `content`: A [files resource](/schema/files-resource.schema.json) - `file`

- Errors:
  - `404`: The folder was not found - `notFound`
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`
  - `501`: Provider not available - `providerNotFound`
