---
title: Placeholders
description: Lista y uso de placeholders internos y de PlaceholderAPI para StorageMechanic.
published: true
date: 2024-03-05T10:45:52.936Z
tags: 
editor: markdown
dateCreated: 2023-10-01T16:33:11.912Z
---

# Placeholders

## Placeholders internos

| **Placeholders**   | **Texto**                                              |
|--------------------|------------------------------------------------------|
| %storage_id%       | Te dice qué almacenamiento tienes abierto              |
| %max_pages%        | Te dice el número total de páginas en ese Almacenamiento. |
| %actual_page%      | Te dice en qué página del Almacenamiento estás.    |

## Placeholder API

| PlaceHolder                | Uso                                 | Cómo usar                                                        |
|----------------------------|-------------------------------------|-------------------------------------------------------------------|
| %smapi_exist_**ID**%       | Usado para ver si existe un id de almacenamiento  | Simplemente donde dice _ID cambiamos el ID por el id del storageAPI |