---
title: Interfaz de elementos - config
description: 
published: true
date: 2025-02-02T00:47:04.119Z
tags: 
editor: undefined
dateCreated: 2023-10-01T21:18:17.880Z
---

# **Interfaz de elementos - config**

**¿Cómo funciona?**

Aquí configuras los bloques que serán usados como interfaz en [Storage-config](/storagemechanics/config/storage-config)

Ubicación del archivo de configuración: **/plugins/StorageMechanic/itemInterfaces/**


| TipoElemento | Uso |
| --- | --- |
| ***NEXT\_PAGE*** | página siguiente |
| ***BACK\_PAGE*** | página anterior |
| ***SEARCH\_PAGE*** | ingresar número de página a ir |
| ***BLOCKED\_ITEM*** | no puedes tomar el elemento |
| ***SEARCH\_ITEM*** | buscar elemento en almacenamiento |
| ***CLEAN\_ITEM*** | limpiar elementos en slots específicos y página |
| ***PLACEHOLDER*** | poner elemento en esta interfaz de elemento |
| ***ACTION*** | ejecutar acción específica |
| **DROP_ITEMS** | Tirará todos los elementos según tu filtro. |
| **COMMAND_ITEM** | Ejecutar un comando al hacer clic en el elemento. |

## Elemento\_bloqueado

Elementos que el jugador no puede mover en la Interfaz

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

## Página siguiente

Elemento para ir a la página siguiente

### ID
`NEXT_PAGE`

```yml
  item3:
    itemType: next_page
    item: 'mc:arrow'
    displayName: '<red>SIGUIENTE'
```

## Página anterior

Elemento para ir a la página anterior

### ID
`BACK_PAGE`

```yml
  item4:
    itemType: back_page
    item: 'mc:arrow'
    displayName: '<red>ATRÁS'
```

## Buscar página

Elemento para buscar una página específica

### ID
`SEARCH_PAGE`

| Propiedad | Uso |
| --- | --- |
| max_distance | Esta es la distancia máxima desde la cual el jugador puede abrir la página desde la ubicación inicial. |

```yml
  item5:
    itemType: search_page
    item: 'mc:stone'
    displayName: '<red>BUSCAR PÁGINA'
    properties:
      max_distance: 5.0
```

## Búsqueda de Elemento

Este elemento será el que usarás para navegar al menú de búsqueda de elementos.

### ID
`ITEM_SEARCH`

## Propiedades

| Propiedad | Uso |
| --- | --- |
| inv-id | El id del menú que se abrirá en caso de que quieras elegir cómo buscar el elemento se define. [Enlace inventario](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples)|
| def-action | Si la acción por defecto no está definida en la propiedad, se abrirá el menú definido en `inv-id`. Los valores por defecto son: **BY_MATERIAL**, **[BY_ITEM_ADAPTER](https://wiki.techmc.es/en/mechanics/adapter)** , **BY_DISPLAY_NAME** |
| inv-anvil-id | El inventario que tiene que abrirse en caso de que el tipo de entrada sea `anvil` [Enlace inventario](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples) |
| inv-result-id | El id del menú que se abrirá si buscas con `SIGN` o al hacer clic en los resultados del Menú `ANVIL` [Enlace inventario](https://wiki.techmc.es/en/storagemechanics/config/inventories-config#yaml-examples) |
| search-input | Tipos de entradas para búsqueda de elementos: **SIGN** , **ANVIL** |

```yml
.
  itemSearch:
    itemType: SEARCH_ITEM #tipo
    item: 'mc:diamond'
    displayName: '<gold>Buscar elementos'
    properties:
      inv-id: search-items
      def-action: BY_MATERIAL #BY_MATERIAL, BY_ITEM_ADAPTER, BY_DISPLAY_NAME
      inv-anvil-id: search-items-anvil
      inv-result-id: search-items-result
      search-input: ANVIL #SIGN, ANVIL
```

## Limpiar elementos

Esto hace que elimine los elementos en los slots o páginas especificados.

### ID
`CLEAN_ITEM`

### Propiedades
| Propiedad | Uso |
| --- | --- |
| pages | Páginas en las que se elimina el contenido en el slot específico |
| slots | Slots en los que se eliminará el contenido |

```yml
  itemCleaner:
    itemType: CLEAN_ITEM
    item: 'mc:stone'
    displayName: '<gold>Limpiar almacenamiento.'
    properties:
      pages: [0-2]
      slots: [0-53]
```

## Elemento PlaceHolder

Este es un elemento que no puede ser removido y solo permitirá que un elemento específico sea colocado encima de él.

### ID
`PLACEHOLDER`

### Propiedades
| Propiedad | Uso |
| --- | --- |
| pages | Páginas en las que el contenido en el slot específico es eliminado |
| slots | Slots en los que se eliminará el contenido |
| items | Lista de elementos que pueden ser colocados |

```yml
  itemPlaceHolder:
    itemType: PLACEHOLDER
    item: 'mc:stone'
    displayName: '<gold>PlaceHolder.'
    properties:
      pages: [0-2]
      slots: [0-53]
      items: 
        - "mc:stone"
```

## Ejecutar acción

Este elemento ejecutará una acción con el sistema de acciones de StorageMechanic.

### ID
`ACTION`

### Propiedades
| Propiedad | Uso |
| --- | --- |
| action | El id de la acción que será ejecutada |

```yml
  itemAction:
    itemType: ACTION
    item: 'mc:diamond'
    displayName: '<gold>Ejecutar acción'
    properties:
      action: accion1
```

## Tirar elementos

Tirará todos los elementos según tu filtro.

### ID
`DROP_ITEMS`

### Propiedades
| Propiedad | Uso |
| --- | --- |
| pages | Páginas que serán afectadas |
| slots | Slots que serán afectados |
| def-action | Acción por defecto que será ejecutada |

```yml
  itemDrop:
    itemType: DROP_ITEMS
    item: 'mc:hopper'
    displayName: '<red>Tirar elementos'
    properties:
      pages: [0-2]
      slots: [0-53]
      def-action: BY_MATERIAL #BY_MATERIAL , BY_ITEM_ADAPTER , BY_DISPLAY_NAME , BY_ACTUAL_PAGE , ALL_PAGES
```

## Elemento de comando

Ejecutar un comando al hacer clic en el elemento.

### ID
`COMMAND_ITEM`

### Propiedades
| Propiedad | Uso |
| --- | --- |
| command | El comando que será ejecutado al hacer clic en el elemento |
| as_console | Si es true, el comando será ejecutado como consola |
| as_op | Si es true, el comando será ejecutado como op |
| delay | Retraso en ticks antes de ejecutar el comando |

## Placeholders

| Placeholder | Uso |
| --- | --- |
| %player_name% | El nombre del jugador que hizo clic en el elemento |
| %player_uuid% | El UUID del jugador que hizo clic en el elemento |

```yml
  itemCommand:
    itemType: COMMAND_ITEM
    item: 'mc:diamond_axe'
    displayName: 'Ejecutar comando'
    properties:
      command: say ¡Hola mundo! # comando
      as_console: true
      as_op: false
      delay: 0
```

## Ejemplo de configuración completa

```yml
items:
  # Elementos básicos de interfaz
  item1:
    itemType: BLOCKED_ITEM
    item: 'mc:gray_stained_glass_pane'
    displayName: '<gray> '
  
  item2:
    itemType: NEXT_PAGE
    item: 'mc:arrow'
    displayName: '<green>Página Siguiente'
    lore:
      - '<gray>Haz clic para ir a la siguiente página'
  
  item3:
    itemType: BACK_PAGE
    item: 'mc:arrow'
    displayName: '<red>Página Anterior'
    lore:
      - '<gray>Haz clic para ir a la página anterior'
  
  # Elementos de búsqueda
  itemSearch:
    itemType: SEARCH_ITEM
    item: 'mc:compass'
    displayName: '<yellow>Buscar Elementos'
    lore:
      - '<gray>Haz clic para buscar elementos'
    properties:
      inv-id: search-items
      def-action: BY_MATERIAL
      inv-anvil-id: search-items-anvil
      inv-result-id: search-items-result
      search-input: ANVIL
  
  # Elemento de limpieza
  itemCleaner:
    itemType: CLEAN_ITEM
    item: 'mc:bucket'
    displayName: '<red>Limpiar Almacenamiento'
    lore:
      - '<gray>Eliminar todos los elementos'
    properties:
      pages: [0-10]
      slots: [0-53]
```