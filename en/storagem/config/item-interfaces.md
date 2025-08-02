---
title: Items interface - config
description: 
published: true
date: 2025-02-02T00:47:04.119Z
tags: 
editor: undefined
dateCreated: 2023-10-01T21:18:17.880Z
---

# **Item interface - config**

**How does it work?**

Here you configure the blocks that will be used as interface in [Storage-config](/storagemechanics/config/storage-config)

Configuration file loc: **/plugins/StorageMechanic/itemInterfaces/**


| ItemType | Usage |
| --- | --- |
| ***NEXT\_PAGE*** | next page |
| ***BACK\_PAGE*** | back page |
| ***SEARCH\_PAGE*** | enter num page to go |
| ***BLOCKED\_ITEM*** | you can't take the item |
| ***SEARCH\_ITEM*** | search item in storage |
| ***CLEAN\_ITEM*** | clear items in specific slots and page |
| ***PLACEHOLDER*** | put item in this item interface |
| ***ACTION*** | execute action specific |
| **DROP_ITEMS** | It will drop all the items according to your filter. |
| **COMMAND_ITEM** | Execute a command when clicking on the item. |

## Blocked\_item

Items which the player cannot move around in the Interface

### ID
`BLOCKED_ITEM`

```yml
Items:
  item1:
    itemType: blocked_item
    item: 'mc:cyan_stained_glass_pane'
    displayName: '<red> '
  item2:
    itemType: blocked_item
    item: 'mc:red_stained_glass_pane'
    displayName: '<red> '
```

## Next page

Item to go to the next page

### ID
`NEXT_PAGE`

```yml
  item3:
    itemType: next_page
    item: 'mc:arrow'
    displayName: '<red>NEXT'
```

## Back page

Item to go to previous page

### ID
`BACK_PAGE`

```yml
  item4:
    itemType: back_page
    item: 'mc:arrow'
    displayName: '<red>BACK'
```

## Search page

Item to search for a specific page

### ID
`SEARCH_PAGE`

| Propertie | Usage |
| --- | --- |
| max_distance | This is the maximum distance the player can open the page from the starting location. |

```yml
  item5:
    itemType: search_page
    item: 'mc:stone'
    displayName: '<red>SEARCH PAGE'
    properties:
      max_distance: 5.0
```

## Item Search

This item will be the one you will use to navigate to the item search menu.

### ID
`ITEM_SEARCH`

## Properties

| Propertie | Usage |
| --- | --- |
| inv-id | The id of the menu that will open in case you want to choose how to search for the item is defined. [Link inventory](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples)|
| def-action | If the default action is not defined in the property, the menu defined in `inv-id` will open. The default values are: **BY_MATERIAL**, **[BY_ITEM_ADAPTER](https://wiki.techmc.es/en/mechanics/adapter)** , **BY_DISPLAY_NAME** |
| inv-anvil-id | The inventory that has to be opened in case the input type is `anvil` [Link inventory](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples) |
| inv-result-id | The id of the menu that will open if you search with `SIGN` or when clicking on the results from `ANVIL` Menu [Link inventory](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples) |
| search-input | Types of entries for item search: **SIGN** , **ANVIL** |

```yml
.
  itemSearch:
    itemType: SEARCH_ITEM #type
    item: 'mc:diamond'
    displayName: '<gold>Search items'
    properties:
      inv-id: search-items
      def-action: BY_MATERIAL #BY_MATERIAL, BY_ITEM_ADAPTER, BY_DISPLAY_NAME
      inv-anvil-id: search-items-anvil
      inv-result-id: search-items-result
      search-input: ANVIL #SIGN, ANVIL
```

## Clean items

This makes it delete the items in the specified slots or pages.

### ID
`CLEAN_ITEM`

### Properties
| Propertie | Usage |
| --- | --- |
| pages | Pages in which the content in the specific slot is deleted |
| slots | Slots in which content will be removed |

```yml
  itemCleaner:
    itemType: CLEAN_ITEM
    item: 'mc:stone'
    displayName: '<gold>Clean storage.'
    properties:
      pages: [0-2]
      slots: [0-53]
```

## PlaceHolder item

This is an item that cannot be removed and will only allow a specific item to be placed on top of it.

### ID
`PLACEHOLDER`


### Properties
| Propertie | Usage |
| --- | --- |
| whitelist | List of items that you can put on top of the placeholder |
| blacklist | List of items that you cannot put on top of the placeholder |

```yml
  itemPlaceHolder:
   itemType: PLACEHOLDER
   item: 'mc:stone'
   displayName: '<gold>Only diamonds.'
   properties:
     whitelist:
       enabled: true
       list:
         - mc:diamond #itemId
         - mc:emerald
         - ia:iasurvival:ruby
     blacklist:
       enabled: false
       list:
         - mc:stone #itemId
```

## Execute action

Execute action as [Item Interface Executator event](https://wiki.techmc.es/en/storagemechanics/actions/events#item-interface-executator).

### ID
`ACTION`

### Properties
| Propertie | Usage |
| --- | --- |
| action_id | the id of the action config |

```yml
  itemAction:
    itemType: ACTION
    item: 'mc:redstone'
    displayName: 'Execute action!'
    properties:
      action_id: action5 # action id config
```


## Drop items

It will drop all the items according to your filter.

### ID
`DROP_ITEMS`

### Properties
| Propertie | Usage |
| --- | --- |
| inv-id | The id of the inventory that will be opened to choose how you want to filter the items dropped. [Link inventory](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples) |
| def-action | If this option is not specified, the selection menu will open to select how you want to filter. If it is enabled, clicking on the item will be filtered by the filter applied here. The possible filters are: **BY_MATERIAL** , **[BY_ITEM_ADAPTER](https://wiki.techmc.es/en/mechanics/adapter)** , **BY_DISPLAY_NAME** , **BY_ACTUAL_PAGE** , **ALL_PAGES** |

```yml
.
  itemItemsDrop:
    itemType: DROP_ITEMS
    item: 'mc:stone'
    displayName: '<gold>Click to open dropMenu.'
    properties:
      inv-id: drop-items
      def-action: BY_MATERIAL #BY_MATERIAL , BY_ITEM_ADAPTER , BY_DISPLAY_NAME , BY_ACTUAL_PAGE , ALL_PAGES
```

## Command item

Execute a command when clicking on the item.

### ID
`COMMAND_ITEM`

### Properties
| Propertie | Usage |
| --- | --- |
| command | The command that will be executed when clicking on the item |
| as_console | If true, the command will be executed as console |
| as_op | If true, the command will be executed as op |
| delay | Delay in ticks before executing the command |

## Placeholders

| Placeholder | Usage |
| --- | --- |
| %player_name% | The name of the player who clicked on the item |
| %player_uuid% | The UUID of the player who clicked on the item |

```yml
  itemCommand:
    itemType: COMMAND_ITEM
    item: 'mc:diamond_axe'
    displayName: 'Execute command'
    properties:
      command: say Hello world! # command
      as_console: true
      as_op: false
      delay: 0
```