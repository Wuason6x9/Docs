---
title: Almacenamiento de elementos - config
description: 
published: true
date: 2024-03-08T21:19:13.280Z
tags: 
editor: undefined
dateCreated: 2023-10-02T00:11:29.383Z
---

# Almacenamiento de elementos - configuración

Ubicación del archivo de configuración: **/plugins/StorageMechanic/types/**

## Propiedades

| Propiedad | Uso |
| --- | --- |
| `isStorageable` | Si es false, no puede ser almacenado en ningún almacenamiento (def: true) |
| `isDamageable` |  Permitir que el almacenamiento sea eliminado  |
| `dropAllItemsOnDeath` |  Te permite liberar todo al suelo cuando eliminas el almacenamiento.  |

## Métodos de apertura

| Método | Uso |
| --- | --- |
| left | abrir con clic izquierdo |
| right | abrir con clic derecho |

## Yaml

```yml
storage:
  item: #furniture, block
    item1:
      storage_id: storage1 #Almacenamiento configurado en storage.yml
      item: "mc:stick"
      open: RIGHT #o LEFT
      properties:
         isDamageable: false
         dropAllItemsOnDeath: false
         isStorageable: false #Funciona para Almacenamiento de Muebles, Almacenamiento de Bloques, Almacenamiento de Elementos
```