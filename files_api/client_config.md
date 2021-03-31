---
layout: home
title: Client Configuration Guidelines
nav_order: 11
parent: Dabbu Files API Specification
grand_parent: Architecture and Specifications
---

# Client Configuration Guidelines

Clients that want to allow the user to switch between different providers may wish to follow the concept of 'drives'. (Like physical drives on your computer - `c:`, `d:`, `e:`, etc.)

Each drive can be linked to a certain provider (or an account with that provider - e.g., different drives for different Google accounts). All the OAuth related tokens and metadata will be stored in a JSON config file against that drive's name.

Each provider will have a certain list of fields needed in the request body and headers. This can be read from [a JSON file](/schema/provider_fields.json), and upon its parsing, relevant fields can be accessed from the JSON config of the client and sent along with the requests. The same file can be parsed to enter the fields required while onboarding the user.
