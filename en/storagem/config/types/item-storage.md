---
title: Item storage - config
description: 
published: true
date: 2024-03-08T21:19:13.280Z
tags: 
editor: undefined
dateCreated: 2023-10-02T00:11:29.383Z
---

# Item storage - configuration

Configuration file loc: **/plugins/StorageMechanic/types/**

## Properties

| Propertie | Usage |
| --- | --- |
| `isStorageable` | If it is false, it cannot be stored in any storage (def: true) |
| `isDamageable` |  Allow storage to be deleted  |
| `dropAllItemsOnDeath` |  Allows you to release everything to the ground when you eliminate the storage.  |

## Open methods

| Method | Usage |
| --- | --- |
| left | open on click left |
| right | open on click right |

## Yaml

```yml
storage:
  item: #furniture, block
    item1:
      storage_id: storage1 #Storage configured in storage.yml
      item: "mc:stick"
      open: RIGHT #or LEFT
      properties:
         isDamageable: false
         dropAllItemsOnDeath: false
         isStorageable: false #Works for Furniture Storage,Block Storage,Item Storage
```