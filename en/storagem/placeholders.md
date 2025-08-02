---
title: Placeholders
description: List and usage of internal and PlaceholderAPI placeholders for StorageMechanic.
published: true
date: 2024-03-05T10:45:52.936Z
tags: 
editor: markdown
dateCreated: 2023-10-01T16:33:11.912Z
---

# Placeholders

## Internal placeholders

| **Placeholders**   | **Text**                                              |
|--------------------|------------------------------------------------------|
| %storage_id%       | It tells you which storage you have open              |
| %max_pages%        | It tells you the total number of pages in that Storage. |
| %actual_page%      | It tells you which page of the Storage you are on.    |

## Placeholder API

| PlaceHolder                | Use                                 | How to use                                                        |
|----------------------------|-------------------------------------|-------------------------------------------------------------------|
| %smapi_exist_**ID**%       | Used to see if a storage id exists  | Simply where it says _ID we change the ID to the id of the storageAPI |
