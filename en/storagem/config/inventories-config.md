---
title: Inventories - config
description: 
published: true
date: 2024-03-10T03:44:33.633Z
tags: 
editor: undefined
dateCreated: 2023-10-01T23:49:35.764Z
---

# **Inventories - config**

This configuration is optional, it is not something to add content, it is simply to be able to modify menus of the plugin itself, in order to make it as customizable as possible, you will be able to customize the menus to your liking.

Configuration file loc: **/plugins/StorageMechanic/inventories/**

### Yaml examples


**Example for menu for anvil search items** (`inv-anvil-id`) [(LINK)](https://wiki.techmc.es/storagemechanics/config/item-interfaces#properties)

```yml
inventories:
  search-items-anvil:
    type: ANVIL
    title: '<white>%img_offset_-60%%img_anvilsearchitem% %img_offset_-200%Search items'
    data_slots: [9-35] #Inventory player slots
    refresh_ticks: 20
    added_to_inventory: '<green>Added to list!'
    result_lore:
      - "<red>Click to get on close!" 
      - "<red>Page: <aqua>%page% <red>slot: <aqua>%slot%"
    items:
      next_page:
        id: NEXT_PAGE #REQUIRED 1
        item: sm:next_page
        slots: [8]
      back_page:
        id: BACK_PAGE #REQUIRED 1
        item: sm:back_page
        slots: [0]
      repair_item:
        id: REPAIR_ITEM #REQUIRED 1
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

**Example for menu for result search items** (`inv-result-id`) [(LINK)](https://wiki.techmc.es/storagemechanics/config/item-interfaces#properties)

```yml
inventories:
  search-items-result:
    type: CHEST
    rows: 6
    title: '<white>%img_offset_-8%%img_anvilsearchresult% %img_offset_-252%Search result:'
    data_slots: [0-44]
    result_lore: 
      - "<red>Page: <aqua>%page% <red>slot: <aqua>%slot%"
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

**Example for menu for select def action for search items** (`inv-id`) [(LINK)](https://wiki.techmc.es/storagemechanics/config/item-interfaces#properties)

```yml
inventories:
  search-items:
    title: '<red>Search Items'
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

**Example for menu for select def action for drop items** (`inv-id`) [(LINK)](https://wiki.techmc.es/en/storagemechanics/config/item-interfaces#drop-items)

```yml
inventories:
  drop-items:
    title: '<red>Drop Items menu'
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