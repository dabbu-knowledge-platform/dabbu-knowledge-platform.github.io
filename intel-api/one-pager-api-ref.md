---
layout: home
title: One Pager API Specification
nav_order: 9
parent: Dabbu Intel API Specification
grand_parent: Architecture and Specifications
---

# Creating a summary regarding a certain topic, person or place from file(s)

**POST** : `/one-pager`

- Request parameters: [Empty]

- Request body: [Posted as multipart form data]

  - `content`: The files to extract info from - `array<file-data>` [Compulsory]

- Response:

  - `code`: The HTTP response code - `number`
  - `error`: Object containing `message` and `reason` fields - `object`
  - `content`: The text summary - `object`

- Errors:
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`
