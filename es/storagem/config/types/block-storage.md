---
title: Almacenamiento de bloques - configuración
description: 
published: true
date: 2024-03-08T21:19:23.497Z
tags: 
editor: undefined
dateCreated: 2023-10-02T00:41:55.366Z
---

# Almacenamiento de bloques - configuración

Ubicación del archivo de configuración: **/plugins/StorageMechanic/types/**

## Propiedades

| **Propiedad** | **Uso** |
| --- | --- |
| isStorageable | Si es false, no puede ser almacenado en ningún almacenamiento (def: true) |
| isBreakable | Si es false, el almacenamiento no puede ser destruido hasta que esté completamente vacío (def: true) |

## Métodos de apertura

| **Método** | **Uso** |
| --- | --- |
| left | abrir con clic izquierdo |
| right | abrir con clic derecho |

## Tipo de almacenamiento de bloque

| **Tipo** | **Uso** |
| --- | --- |
| chest | (Igual que un Cofre) |
| shulker | Cuando se rompe, todos los elementos dentro del bloque serán almacenados en el elemento tirado, hasta que sea **r**eposicionado (igual que un shulker) |
| ender\_chest | (Igual que un Cofre del End) |
| personal | Es un tipo de Cofre del End pero en lugar de ser global, solo permanecerá en ese bloque, cada persona tendrá un inventario diferente en ese bloque pero si colocan el mismo bloque en otro lugar tendrá un almacenamiento diferente |

## Mecánicas

### Tolva

ID: `hopper_mechanic`

| **Propiedad** | **Uso** |
| --- | --- |
| `transfer_tick` | cada cuántos ticks se ejecuta (def: 8) |
| `transfer_amount` | la cantidad que se transfiere cada ticks configurados (def: 1) |

## YAML

```yml
storage:
  block: #item, furniture
    blockstorage1:
      storage_id: storage1 #Almacenamiento configurado en storage.yml
      block: "sm:block1" #id del bloque que se convertirá en almacenamiento
      open: RIGHT #o LEFT
      type: ENDER_CHEST #SHULKER, CHEST, PERSONAL
      properties:
        isBreakable: true #Si puede romperse o no
      mechanics:
        hopper_mechanic:
          enabled: true
          properties:
            transfer_tick: 8
            transfer_amount: 1
```