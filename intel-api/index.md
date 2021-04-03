---
layout: home
title: Dabbu Intel API Specification
nav_order: 6
parent: Architecture and Specifications
has_children: true
---

# Dabbu Intel API Specification

Dabbu Intel API is a REST API to extract topics, people and places from various files (docx, pptx, xlsx, pdf and plain text content) and summarize the content in files regarding a certain topic. You can access these APIs using **simple HTTP requests.**

## Supported HTTP methods

There are several actions you can perform on resources by making HTTP requests to the API. Dabbu allows you to perform the following actions:

- extract topics, people and places from uploaded files [POST]
- create a summary (one pager) from uploaded files based on a certain topic found in those files [POST]
