---
layout: home
title: Extract Info API Specification
nav_order: 8
parent: Dabbu Intel API Specification
grand_parent: API Reference
---

# Extracting topics, people and places from file(s)

**POST** : `/extract-info`

- Request parameters: [Empty]

- Request body: [Posted as multipart form data]

  - `content`: The files to extract info from - `array<file-data>` [Compulsory]

- Response:

  - `code`: The HTTP response code - `number`
  - `error`: Object containing `message` and `reason` fields - `object`
  - `content`: Three arrays of objects, one each for `topics` (fields: `text` and `file`), `people` (fields: `email` and `file`) and `places` (fields: `place` and `file`) - `object`

- Errors:
  - `500`: Internal server error, used if an uncaught exception appears - `internalServerError`
