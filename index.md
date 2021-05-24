---
layout: default
title: Home
nav_order: 1
---

# Introduction

With the Dabbu Knowledge Platform, we aim to rethink the way we organize and traverse large amounts of knowledge, no matter where it is stored.

Dabbu allows you to access any of your personal information (Gmail, Google Drive, OneDrive, your hard drive, ...) as simple files and folders from Dabbu CLI.

It not only allows you to seamlessly search/traverse your information across these sources (as simple as `cd`, `list`), but also move information around between drives (`copy`) - yes even your Gmail messages in a thread get copied to your hard drive as `.md` files in a zip if you do a `harddrive:/$ cp gmail:/INBOX/ ./"My Emails"`.

You can also go into the special knowledge drive where you can pivot information by topics/people/places e.g. `knowledge:/$ cd austin` (will return you all your information from Gmail, Google Drive, OneDrive that has a reference to the place Austin). You can further narrow your search by doing `knowledge:/austin$ cd ravi@example.com` (yes it even extracts people and allows you to pivot information by them). This would show you all emails and files that are related to Austin and from/to ravi@example.com.

All of this has been implemented by abstracting access to providers (you can add more providers as modules) and exposing a unified API for information (no matter where and what form it takes).

The only way to use Dabbu (at the moment) is through a command-line interface (CLI). A desktop interface is in the works.
