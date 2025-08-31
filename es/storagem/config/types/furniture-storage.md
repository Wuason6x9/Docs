---
title: Almacenamiento de muebles - configuración
description: 
published: true
date: 2024-03-08T16:52:03.368Z
tags: 
editor: undefined
dateCreated: 2023-10-02T00:30:22.664Z
---

# Almacenamiento de muebles - configuración

Ubicación del archivo de configuración: **/plugins/StorageMechanic/types/**

## Propiedades

| **Propiedad** | **Uso** |
| --- | --- |
| isStorageable | Si es false, no puede ser almacenado en ningún almacenamiento (def: true) |
| isBreakable | Si es false, el almacenamiento no puede ser destruido hasta que esté completamente vacío (def: true) |

## Tipo de almacenamiento de muebles

| Tipo | **Uso** |
| --- | --- |
| chest | (Igual que un Cofre) |
| shulker | Cuando se rompe, todos los elementos dentro del bloque serán almacenados en el elemento tirado, hasta que sea **r**eposicionado (igual que un shulker) |
| ender\_chest | (Igual que un Cofre del End) |
| personal | Es un tipo de Cofre del End pero en lugar de ser global, solo permanecerá en ese bloque, cada persona tendrá un inventario diferente en ese bloque pero si colocan el mismo bloque en otro lugar tendrá un almacenamiento diferente |

## Métodos de apertura

| **Método** | **Uso** |
| --- | --- |
| left | abrir con clic izquierdo |
| right | abrir con clic derecho |

## YAML

```yml
storage:
  furniture:
    furnituretorage5:
      storage_id: storage1
      furniture: "ia:elitefantasy:TestBlock"
      open: RIGHT #o LEFT
      type: SHULKER
      properties:
        isBreakable: false
```