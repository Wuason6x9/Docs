---
title: Storage - Configuration
description: 
published: true
date: 2024-03-10T14:01:58.677Z
tags: 
editor: undefined
dateCreated: 2023-10-01T22:23:36.669Z
---

# **Storage - Configuration**

How does it work?

This section for example in `storage1` will be a storage type, so when you create a block with storage and put `storage1` it will have all these settings in the storage you created.

Configuration file loc: **/plugins/StorageMechanic/storages/**

## Things to keep in mind

1.  It is always necessary to specify the slot and the page
2.  You should never go beyond the slots because an error will appear if there is a chest that has 6 rows the range will be 0-53 always starting from 0-final number - 1
3.  You should always keep in mind to place the pages where you want it to be. Keep in mind the range goes from 0 to the last page of your maximum number of pages but with - 1

## Configuration - section

### Config

| Option | Usage | default value |
| --- | --- | --- |
| max_views | This adjusts the maximum number of players that can be viewing the storage at the same time. if it is -1 the system is not activated | `-1` |

### Inventory types

| Type | Usage | Slots |
| --- | --- | --- |
| **chest** | **Chest type inventory** | `**size: 54 slots**` |
| dropper | Dropper type inventory | `size: 9 slots` |
| hopper | Hopper type inventory | `size: 5 slots` |
| dispenser | Dispenser type inventory | `size: 9 slots` |

### Properties
| Propertie | Usage | required |
| --- | --- | --- |
| isTempStorage | recommended for use actions only no storage persistent | No |
| dropAllItemsOnClose | recommended for use actions only no storage persistent | No |

> Be careful how many pages you use could affect performance. 
I have tried an inventory with 1000 pages without problem but be careful especially if you use mysql
{.is-warning}

### Things to keep in mind

1.  Only if you create a type chest inventory will they be able to modify the rows
2.  You can add up to 2147483646 pages
3.  By default if you do not modify anything in chest you will have 54 slots = 6 rows
4.  You don't need to have rows if you are not using chest as a type
5.  If you do not put a title it will be automatically "untitled"
6.  storage id cannot contain "\_"

### YAML

```yml
storages:
  storage1: #Storage ID
  	config:
    	max_views: -1
    storage:
      rows: 6
      pages: 10 #Pages that the storage will have
      inventory_type: chest #dropper, hopper, dispenser 
      title: "Storage (%actual_page%/%max_pages%)" #Menu Title
      properties:
        isTempStorage: false # for use actions only no storage persistent
        dropAllItemsOnClose: false # for use actions only no storage persistent
```

## Sounds - section

### Types

| Type | Usage |
| --- | --- |
| close | on close page |
| open | on open page |
| click | on click slot |

### Things to keep in mind

1.  Remember to specify the pages

### YAML

```yml
.
    sounds:
      enabled: true
      list:
        sound_1:
          type: close #Sound when closing the storage
          pages: [0,1]
          sound: 'minecraft:block.barrel.close'
        sound_2:
          type: open #Sound when opening the storage
          pages: [0,1]
          sound: 'minecraft:block.barrel.open'
        sound_3:
          type: click #Sound when click the storage
          pages: [0,1]
          slots: [0]
          sound: 'minecraft:sound'
```

## Items default - section

The first time you open a new Storage of this type, the items you choose will be placed inside and can be obtained.

### Things to keep in mind

1.  Remember to specify the pages
2.  the amount range is from 1 - 64
3.  The chance range is from 0 - 100 in decimals
4.  Remember that items: is a list and you can enter adapters id

### YAML

```yml
.
    items: 
      default:
        enabled: true
        list:
          item_1:
            pages: [0,1] #Slots in which they will be
            slots: [0]
            amount: 10-40 #amount that may appear
            chance: 40 #% in which it will appear
            items: 
              - "mc:stone"
```

## Items block - section

Used to lock items slots without item interface

### Things to keep in mind

1.  Remember to specify the pages
2.  If you want the message not to appear, simply delete that line

### YAML

```yml
.
      block:
        enabled: true
        list:
          block1:
            pages: [ 0,1 ]
            slots: [ 0,1 ]
            message: "test"
```

## White list - section

Items can be placed in Storage

### Things to keep in mind

1.  Remember to specify the pages

### YAML

```yml
.
      whitelist: 
        enabled: false
        message: "It is not in the white list!"
        list:
          items_1:
            pages: [0,1] #Only on this page of the Storage this configuration will be valid.
            slots: [0-20] #Slots in which they will be
            items:
              - 'mc:diamond'
              - 'mc:emerald'
```

## Black list - section

Items that may not be place inside the Storage

### Things to keep in mind

1.  Remember to specify the pages

### YAML

```yml
.
      blacklist:
        enabled: true
        message: "It is on the blacklist!"
        list:
          items_test:
            pages: [1] #Only on this page of the Storage this configuration will be valid.
            slots: [0-53] #Slots in which they will be
            items:
              - 'mc:emerald'
```

## Interfaces - section

These are the items that will be the default items in the interface, these are configured in [ItemInterface](/storagemechanics/config/item-interfaces)

### Things to keep in mind

1.  Remember to specify the pages

### YAML

```yml
.
    interfaces:
      enabled: true
      list:
        iterface1:
          pages: [0,2,4,6,8] #pages on which they will be
          slots: [0-9,44-53,17,26,35,36,27,18] #Slots in which they will be
          item: item1 #item1 in iteminterface.yml
        iterface2:
          pages: [1,3,5,7,9]
          slots: [0-9,44-53,17,26,35,36,27,18] #Slots in which they will be
          item: item2 #item2 in iteminterface.yml
        iterface3:
          pages: [0-8] 
          slots: [52]
          item: item3 #item3 in iteminterface.yml
        iterface4:
          pages: [1-9] #pages on which they will be
          slots: [51]
          item: item4 #item4 in iteminterface.yml
        iterface5:
          pages: [1-9] #pages on which they will be
          slots: [50]
          item: item5 #item5 in iteminterface.yml
```

## Stages - section

Stages are used to give status to the inventory either to change the title every second or to change the content of the item interfaces.

### Things to keep in mind

1.  Remember to specify the pages
2.  If you put it in refresh:0 you can use it with the actions system of the plugin itself
3.  Running async means it will be fine
4.  You can change whatever you want, if you want to change only the title, delete the interfaces section and vice versa, if you want to only change the interfaces, remove the title line.
5.  Note that this runs from top to bottom

### YAML

```yml
.
    stages:
      refresh: 0
      list:
        stage_1:
          title: "<red>Stage 1"
          interfaces:
            list:
              item_action:
                pages: [0-2]
                slots: [22]
                item: itemAction
              next_page:
                pages: [0-1] 
                slots: [53]
                item: item3 #item3 in iteminterface.yml
              back_page:
                pages: [1-2] #pages on which they will be
                slots: [52]
                item: item4 #item4 in iteminterface.yml
              search_page:
                pages: [0-2] #pages on which they will be
                slots: [46]
                item: item5 #item5 in iteminterface.yml
              placeholder:
                pages: [0] #pages on which they will be
                slots: [0-8]
                item: itemPlaceHolder #item5 in iteminterface.yml
              clear_inventory:
                pages: [0-2] #pages on which they will be
                slots: [47]
                item: itemCleaner #item5 in iteminterface.yml
              search_item:
                pages: [0-2] #pages on which they will be
                slots: [45]
                item: itemSearch #item5 in iteminterface.yml
```

## Yaml Configuration example

```yml
storages:
  storage1: #Storage ID
  	config:
    	max_views: -1
    storage:
      rows: 6
      pages: 10 #Pages that the storage will have
      inventory_type: chest #dropper, hopper, dispenser 
      title: "Storage (%actual_page%/%max_pages%)" #Menu Title
    sounds:
      enabled: true
      list:
        sound_1:
          type: close #Sound when closing the storage
          pages: [0,1]
          sound: 'minecraft:block.barrel.close'
        sound_2:
          type: open #Sound when opening the storage
          pages: [0,1]
          sound: 'minecraft:block.barrel.open'
        sound_3:
          type: click #Sound when click the storage
          pages: [0,1]
          slots: [0]
          sound: 'minecraft:sound'
    items: 
      default:
        enabled: true
        list:
          item_1:
            pages: [0,1] #Slots in which they will be
            slots: [0]
            amount: 10-40 #amount that may appear
            chance: 40 #% in which it will appear
            items: 
              - "mc:stone"
      block:
        enabled: true
        list:
          block1:
            pages: [ 0,1 ]
            slots: [ 0,1 ]
            message: "test"
      whitelist: 
        enabled: false
        message: "It is not in the white list!"
        list:
          items_1:
            pages: [0,1] #Only on this page of the Storage this configuration will be valid.
            slots: [0-20] #Slots in which they will be
            items:
              - 'mc:diamond'
              - 'mc:emerald'
      blacklist:
        enabled: true
        message: "It is on the blacklist!"
        list:
          items_test:
            pages: [1] #Only on this page of the Storage this configuration will be valid.
            slots: [0-53] #Slots in which they will be
            items:
              - 'mc:emerald'
    interfaces:
      enabled: true
      list:
        iterface1:
          pages: [0,2,4,6,8] #pages on which they will be
          slots: [0-9,44-53,17,26,35,36,27,18] #Slots in which they will be
          item: item1 #item1 in iteminterface.yml
        iterface2:
          pages: [1,3,5,7,9]
          slots: [0-9,44-53,17,26,35,36,27,18] #Slots in which they will be
          item: item2 #item2 in iteminterface.yml
        iterface3:
          pages: [0-8] 
          slots: [52]
          item: item3 #item3 in iteminterface.yml
        iterface4:
          pages: [1-9] #pages on which they will be
          slots: [51]
          item: item4 #item4 in iteminterface.yml
        iterface5:
          pages: [1-9] #pages on which they will be
          slots: [50]
          item: item5 #item5 in iteminterface.yml
    stages:
      refresh: 0
      list:
        stage_1:
          title: "<red>Stage 1"
          interfaces:
            list:
              item_action:
                pages: [0-2]
                slots: [22]
                item: itemAction
              next_page:
                pages: [0-1] 
                slots: [53]
                item: item3 #item3 in iteminterface.yml
              back_page:
                pages: [1-2] #pages on which they will be
                slots: [52]
                item: item4 #item4 in iteminterface.yml
              search_page:
                pages: [0-2] #pages on which they will be
                slots: [46]
                item: item5 #item5 in iteminterface.yml
              placeholder:
                pages: [0] #pages on which they will be
                slots: [0-8]
                item: itemPlaceHolder #item5 in iteminterface.yml
              clear_inventory:
                pages: [0-2] #pages on which they will be
                slots: [47]
                item: itemCleaner #item5 in iteminterface.yml
              search_item:
                pages: [0-2] #pages on which they will be
                slots: [45]
                item: itemSearch #item5 in iteminterface.yml
```