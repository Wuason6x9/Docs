---
title: Elementos personalizados - config
description: 
published: true
date: 2024-08-09T17:45:35.888Z
tags: 
editor: undefined
dateCreated: 2024-03-10T02:29:04.090Z
---

# Elementos personalizados - config

¡Crea tus propios elementos StorageMechanics desde elementos vanilla!

Ubicación del archivo de configuración: **/plugins/StorageMechanic/CustomItems/**

## Propiedades
| Propiedad | Uso |
| --- | --- |
| `drop_block` | tirar bloque al romper |
| `stackable` | Si quieres que se apile o no |
| `skull_texture` | Especificar una textura para la cabeza en caso de que sea una cabeza de jugador. |

## Ejemplo de configuración

```yml
items:
  item1:
    item: 'mc:player_head' # id del elemento adaptador
    displayName: 'MOCHILA'
    lore:
      - '<green> LORE DE PRUEBA'
    properties:
      drop_block: true #Si quieres que libere el bloque al romper
      stackable: false #Es útil en caso de que queramos que sea un elemento único.
      skull_texture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvODg3MGJlOTA3NjVjMWYzOTBmODc3Yzk2YTQ0OTUwMWRmNjQxYjhjNmY2OTEwMjgxNDBmMGFhYzc3MjAwNWYyMyJ9fX0=
```