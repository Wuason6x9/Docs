---
title: Custom items - config
description: 
published: true
date: 2024-08-09T17:45:35.888Z
tags: 
editor: undefined
dateCreated: 2024-03-10T02:29:04.090Z
---

# Custom items - config

Create your own StorageMechanics items from vanilla items!

Configuration file loc: **/plugins/StorageMechanic/CustomItems/**

## Properties
| Propertie | Usage |
| --- | --- |
| `drop_block` | drop block on break |
| `stackable` | Whether you want to stack or not |
| `skull_texture` | Specify a texture for the head in case it is a player's head. |

## Configuration example

```yml
items:
  item1:
    item: 'mc:player_head' # adapter item id
    displayName: 'BACK PACK'
    lore:
      - '<green> TEST LORE'
    properties:
      drop_block: true #If you want it to release the block when breaking
      stackable: false #It is useful in case we want it to be a unique item.
      skull_texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvODg3MGJlOTA3NjVjMWYzOTBmODc3Yzk2YTQ0OTUwMWRmNjQxYjhjNmY2OTEwMjgxNDBmMGFhYzc3MjAwNWYyMyJ9fX0=
```