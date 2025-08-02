---
title: Block storage - configuration
description: 
published: true
date: 2024-03-08T21:19:23.497Z
tags: 
editor: undefined
dateCreated: 2023-10-02T00:41:55.366Z
---

# Block storage - configuration

Configuration file loc: **/plugins/StorageMechanic/types/**

## Properties

| **Propertie** | **Usage** |
| --- | --- |
| isStorageable | If it is false, it cannot be stored in any storage (def: true) |
| isBreakable | If it is false, the storage cannot be destroyed until it is completely empty (def: true) |

## Open methods

| **Method** | **Usage** |
| --- | --- |
| left | open on click left |
| right | open on click right |

## Block storage type

| **Type** | **Usage** |
| --- | --- |
| chest | (Same as an Chest) |
| shulker | When broken, all items inside the block will be stored in the dropped item, until it is **r**epositioned(same as a shulker) |
| ender\_chest | (Same as an Ender Chest) |
| personal | It is a kind of Ender Chest but instead of being global, it will only stay in that block, each person will have a different inventory in that block but if they place the same block somewhere else it will have a different storage |

## Mechanics

### Hopper

ID: `hopper_mechanic`

| **Propertie** | **Usage** |
| --- | --- |
| `transfer_tick` | every few ticks it executes (def: 8) |
| `transfer_amount` | the amount that is transferred each configured ticks (def: 1) |

## YAML

```yml
storage:
  block: #item, furniture
    blockstorage1:
      storage_id: storage1 #Storage configured in storage.yml
      block: "sm:block1" #id of the block that will become storage
      open: RIGHT #or LEFT
      type: ENDER_CHEST #SHULKER, CHEST, PERSONAL
      properties:
        isBreakable: true #Whether it can break or not
      mechanics:
        hopper_mechanic:
          enabled: true
          properties:
            transfer_tick: 8
            transfer_amount: 1
```