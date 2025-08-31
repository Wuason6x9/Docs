---
title: Inventarios - config
description: 
published: true
date: 2024-03-10T03:44:33.633Z
tags: 
editor: undefined
dateCreated: 2023-10-01T23:49:35.764Z
---

# **Inventarios - config**

Esta configuración es opcional, no es algo para agregar contenido, es simplemente para poder modificar menús del propio plugin, con el fin de hacerlo lo más personalizable posible, podrás personalizar los menús a tu gusto.

Ubicación del archivo de configuración: **/plugins/StorageMechanic/inventories/**

### Ejemplos Yaml


**Ejemplo para menú de búsqueda de elementos en yunque** (`inv-anvil-id`) [(ENLACE)](https://wiki.techmc.es/storagemechanics/config/item-interfaces#properties)

```yml
inventories:
  search-items-anvil:
    type: ANVIL
    title: '<white>%img_offset_-60%%img_anvilsearchitem% %img_offset_-200%Buscar elementos'
    data_slots: [9-35] #Slots del inventario del jugador
    refresh_ticks: 20
    added_to_inventory: '<green>¡Agregado a la lista!'
    result_lore:
      - "<red>¡Haz clic para obtener al cerrar!" 
      - "<red>Página: <aqua>%page% <red>slot: <aqua>%slot%"
    items:
      next_page:
        id: NEXT_PAGE #REQUERIDO 1
        item: sm:next_page
        slots: [8]
      back_page:
        id: BACK_PAGE #REQUERIDO 1
        item: sm:back_page
        slots: [0]
      repair_item:
        id: REPAIR_ITEM #REQUERIDO 1
        item: sm:empty_item
      open_result_inv_item:
        id: OPEN_RESULT
        item: sm:item_open_result
        slots: [3]
      research_item:
        id: RESEARCH_ITEM
        item: sm:search_item
        slots: [5]
```

**Ejemplo para menú de resultado de búsqueda de elementos** (`inv-result-id`) [(ENLACE)](https://wiki.techmc.es/storagemechanics/config/item-interfaces#properties)

```yml
inventories:
  search-items-result:
    type: CHEST
    rows: 6
    title: '<white>%img_offset_-8%%img_anvilsearchresult% %img_offset_-252%Resultado de búsqueda:'
    data_slots: [0-44]
    result_lore: 
      - "<red>Página: <aqua>%page% <red>slot: <aqua>%slot%"
    items:
      next_page:
        id: NEXT_PAGE
        item: sm:next_page
        slots: [53]
      back_page:
        id: BACK_PAGE
        item: sm:back_page
        slots: [45]
```

**Ejemplo para menú de selección de acción predeterminada para búsqueda de elementos** (`inv-id`) [(ENLACE)](https://wiki.techmc.es/storagemechanics/config/item-interfaces#properties)

```yml
inventories:
  search-items:
    title: '<red>Buscar Elementos'
    type: HOPPER
    items:
      item0:
        id: blocked
        item: sm:blocked_item
        slots: [0-4]
      item1:
        id: BY_MATERIAL
        item: sm:item_byMaterial
        slots: [1]
      item2:
        id: BY_DISPLAY_NAME 
        item: sm:item_byDisplayName
        slots: [2]
      item3:
        id: BY_ITEM_ADAPTER
        item: sm:item_byItemAdapter
        slots: [3]
```

**Ejemplo para menú de selección de acción predeterminada para tirar elementos** (`inv-id`) [(ENLACE)](https://wiki.techmc.es/en/storagemechanics/config/item-interfaces#drop-items)

```yml
inventories:
  drop-items:
    title: '<red>Menú Tirar Elementos'
    type: HOPPER
    items:
      item1:
        id: BY_MATERIAL
        item: sm:item_byMaterial
        amount: 1
        slots: [0]
      item3:
        id: BY_ITEM_ADAPTER
        item: sm:item_byItemAdapter
        amount: 1
        slots: [1]
      item4:
        id: BY_DISPLAY_NAME 
        item: sm:item_byDisplayName
        amount: 1
        slots: [2]
      item5:
        id: BY_ACTUAL_PAGE 
        item: sm:item_byActualPage
        amount: 1
        slots: [3]
      item6:
        id: ALL_PAGES
        item: sm:item_allPages
        amount: 1
        slots: [4]
```