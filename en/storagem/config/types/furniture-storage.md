---
title: Furniture storage - configuration
description: 
published: true
date: 2024-03-08T16:52:03.368Z
tags: 
editor: undefined
dateCreated: 2023-10-02T00:30:22.664Z
---

# Furniture storage - configuration

Configuration file loc: **/plugins/StorageMechanic/types/**

## Properties

| **Propertie** | **Usage** |
| --- | --- |
| isStorageable | If it is false, it cannot be stored in any storage (def: true) |
| isBreakable | If it is false, the storage cannot be destroyed until it is completely empty (def: true) |

## Furniture storage type

| Type | **Usage** |
| --- | --- |
| chest | (Same as an Chest) |
| shulker | When broken, all items inside the block will be stored in the dropped item, until it is **r**epositioned (same as a shulker) |
| ender\_chest | (Same as an Ender Chest) |
| personal | It is a kind of Ender Chest but instead of being global, it will only stay in that block, each person will have a different inventory in that block but if they place the same block somewhere else it will have a different storage |

## Open methods

| **Method** | **Usage** |
| --- | --- |
| left | open on click left |
| right | open on click right |

## YAML

```yml
storage:
  furniture:
    furnituretorage5:
      storage_id: storage1
      furniture: "ia:elitefantasy:TestBlock"
      open: RIGHT #or LEFT
      type: SHULKER
      properties:
        isBreakable: false
```