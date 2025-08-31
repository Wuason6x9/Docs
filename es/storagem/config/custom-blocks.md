---
title: Bloques personalizados - config
description: 
published: true
date: 2023-12-18T09:34:23.388Z
tags: 
editor: undefined
dateCreated: 2023-10-01T21:32:47.717Z
---

# Bloques personalizados - config

¡Crea tus propios elementos StorageMechanics desde elementos vanilla!

Ubicación del archivo de configuración: **/plugins/Mechanics/configs/StorageMechanic/CustomBlocks/**

## Propiedades
| Propiedad | Uso |
| --- | --- |
| `drop_block` | tirar bloque al romper |
| `stackable` | Si quieres que se apile o no |

## Ejemplo de configuración

```yml
blocks:
  block1:
    material: 'mc:{id:"minecraft:stone",Count:1b,tag:{Enchantments:[{id:"minecraft:efficiency",lvl:1s}]}}' # id del elemento adaptador
    displayName: 'MOCHILA'
    lore:
      - '<green> LORE DE PRUEBA'
    properties:
      drop_block: true #Si quieres que libere el bloque al romper
      stackable: false #Es útil en caso de que queramos que sea un elemento único.
```