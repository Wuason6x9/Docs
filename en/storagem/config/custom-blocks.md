---
title: Custom blocks - config
description: 
published: true
date: 2023-12-18T09:34:23.388Z
tags: 
editor: undefined
dateCreated: 2023-10-01T21:32:47.717Z
---

# Custom blocks - config

Create your own StorageMechanics items from vanilla items!

Configuration file loc: **/plugins/Mechanics/configs/StorageMechanic/CustomBlocks/**

## Properties
| Propertie | Usage |
| --- | --- |
| `drop_block` | drop block on break |
| `stackable` | Whether you want to stack or not |

## Configuration example

```yml
blocks:
  block1:
    material: 'mc:{id:"minecraft:stone",Count:1b,tag:{Enchantments:[{id:"minecraft:efficiency",lvl:1s}]}}' # adapter item id
    displayName: 'BACK PACK'
    lore:
      - '<green> TEST LORE'
    properties:
      drop_block: true #If you want it to release the block when breaking
      stackable: false #It is useful in case we want it to be a unique item.
```