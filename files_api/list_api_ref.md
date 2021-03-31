---
layout: home
title: List API Specification
nav_order: 6
parent: Dabbu Files API Specification
grand_parent: Architecture and Specifications
---

# Listing files and folders in a specific folder

**GET** : `/data/:providerId/:folderPath`

- Request parameters: [Compulsory]

  - `providerId`: Provider ID - `string`
  - `folderPath`: Path to folder - `string`

- Query parameters: [Optional]

  - `compareWith`: Compare items by a field (specify field name) - `string`
  - `operator`: Only take items with value equal to, less than or greater than the value specified - `enum<string> - =, <, >`
  - `value`: The value of the field the item must be equal to, less than or greater than - `string`
  - `orderBy`: Order by a field (specify field name) - `string`
  - `direction`: The order in which to sort the items - `enum<string> - asc, desc`
  - `exportType`: Type of URI that the content should be returned in; `view` for opening it in the provider's editor, `media` for a download link, other values may be accepted by the provider - `string`

- Request body: [Optional]

  - The request body may contain any fields that the provider requires to execute the request

- Response:

  - `code`: The HTTP response code (200 if successful) - `number`
  - `error`: Object containing `message` and `reason` fields - `object`
  - `content`: Array of [files resources](/schema/files_resource.schema.json) - `array<file>`

- Errors:
  - `400`: Bad URL, invalid syntax for query parameters - `malformedURL`
  - `404`: The folder was not found - `notFound`
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`
  - `501`: Provider not available - `providerNotFound`
