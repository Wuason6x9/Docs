---
title: Almacenamiento - Configuración
description: 
published: true
date: 2024-03-10T14:01:58.677Z
tags: 
editor: undefined
dateCreated: 2023-10-01T22:23:36.669Z
---

# **Almacenamiento - Configuración**

¿Cómo funciona?

Esta sección por ejemplo en `storage1` será un tipo de almacenamiento, así que cuando crees un bloque con almacenamiento y pongas `storage1` tendrá todas estas configuraciones en el almacenamiento que creaste.

Ubicación del archivo de configuración: **/plugins/StorageMechanic/storages/**

## Cosas a tener en cuenta

1.  Siempre es necesario especificar el slot y la página
2.  Nunca debes sobrepasar los slots porque aparecerá un error, si hay un cofre que tiene 6 filas el rango será 0-53 siempre empezando desde 0-número final - 1
3.  Siempre debes tener en cuenta colocar las páginas donde quieres que esté. Ten en cuenta que el rango va desde 0 hasta la última página de tu número máximo de páginas pero con - 1

## Configuración - sección

### Config

| Opción | Uso | valor por defecto |
| --- | --- | --- |
| max_views | Esto ajusta el número máximo de jugadores que pueden estar viendo el almacenamiento al mismo tiempo. si es -1 el sistema no está activado | `-1` |

### Tipos de inventario

| Tipo | Uso | Slots |
| --- | --- | --- |
| **chest** | **Inventario tipo cofre** | `**tamaño: 54 slots**` |
| dropper | Inventario tipo lanzador | `tamaño: 9 slots` |
| hopper | Inventario tipo tolva | `tamaño: 5 slots` |
| dispenser | Inventario tipo dispensador | `tamaño: 9 slots` |

### Propiedades
| Propiedad | Uso | requerido |
| --- | --- | --- |
| isTempStorage | recomendado para usar acciones solo, no almacenamiento persistente | No |
| dropAllItemsOnClose | recomendado para usar acciones solo, no almacenamiento persistente | No |

> Ten cuidado con cuántas páginas usas, podría afectar el rendimiento. 
He probado un inventario con 1000 páginas sin problema pero ten cuidado especialmente si usas mysql
{.is-warning}

### Cosas a tener en cuenta

1.  Solo si creas un inventario tipo cofre podrán modificar las filas
2.  Puedes agregar hasta 2147483646 páginas
3.  Por defecto si no modificas nada en el cofre tendrás 54 slots = 6 filas
4.  No necesitas tener filas si no estás usando cofre como tipo
5.  Si no pones un título será automáticamente "untitled"
6.  el id de almacenamiento no puede contener "\_"

### YAML

```yml
storages:
  storage1: #ID de Almacenamiento
  	config:
    	max_views: -1
    storage:
      rows: 6
      pages: 10 #Páginas que tendrá el almacenamiento
      inventory_type: chest #dropper, hopper, dispenser 
      title: "Storage (%actual_page%/%max_pages%)" #Título del Menú
      properties:
        isTempStorage: false # para usar acciones solo, no almacenamiento persistente
        dropAllItemsOnClose: false # para usar acciones solo, no almacenamiento persistente
```

## Sonidos - sección

### Tipos

| Tipo | Uso |
| --- | --- |
| close | al cerrar página |
| open | al abrir página |
| click | al hacer clic en slot |

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas

### YAML

```yml
.
    sounds:
      enabled: true
      list:
        sound_1:
          type: close #Sonido al cerrar el almacenamiento
          pages: [0,1]
          sound: 'minecraft:block.barrel.close'
        sound_2:
          type: open #Sonido al abrir el almacenamiento
          pages: [0,1]
          sound: 'minecraft:block.barrel.open'
        sound_3:
          type: click #Sonido al hacer clic en el almacenamiento
          pages: [0,1]
          slots: [0]
          sound: 'minecraft:sound'
```

## Elementos por defecto - sección

La primera vez que abres un nuevo Almacenamiento de este tipo, los elementos que elijas serán colocados dentro y podrán ser obtenidos.

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas
2.  el rango de cantidad es de 1 - 64
3.  El rango de posibilidad es de 0 - 100 en decimales
4.  Recuerda que items: es una lista y puedes ingresar IDs de adaptadores

### YAML

```yml
.
    items: 
      default:
        enabled: true
        list:
          item_1:
            pages: [0,1] #Slots en los que estarán
            slots: [0]
            amount: 10-40 #cantidad que puede aparecer
            chance: 40 #% en el que aparecerá
            items: 
              - "mc:stone"
```

## Elementos de bloque - sección

Estos son los elementos que podrás obtener de los bloque-almacenamientos que obtienes al romper el bloque.

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas
2.  el rango de cantidad es de 1 - 64
3.  El rango de posibilidad es de 0 - 100 en decimales
4.  Recuerda que items: es una lista y puedes ingresar IDs de adaptadores

### YAML

```yml
.
    items: 
      block:
        enabled: true
        list:
          item_1:
            pages: [0,1] #Slots en los que estarán
            slots: [0]
            amount: 10-40 #cantidad que puede aparecer
            chance: 40 #% en el que aparecerá
            items: 
              - "mc:stone"
```

## Lista blanca - sección

Solo los elementos especificados en la lista blanca podrán ser colocados en el almacenamiento.

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas

### YAML

```yml
.
    whitelist:
      enabled: true
      list:
        whitelist_1:
          pages: [0,1] #páginas en las que estarán
          slots: [0] #Slots en los que estarán
          items: 
            - "mc:stone"
```

## Lista negra - sección

Los elementos especificados en la lista negra NO podrán ser colocados en el almacenamiento.

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas

### YAML

```yml
.
    blacklist:
      enabled: true
      list:
        blacklist_1:
          pages: [0,1] #páginas en las que estarán
          slots: [0] #Slots en los que estarán
          items: 
            - "mc:stone"
```

## Interfaces - sección

Estos son los elementos que serán los elementos por defecto en la interfaz, estos se configuran en [ItemInterface](/storagemechanics/config/item-interfaces)

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas

### YAML

```yml
.
    interfaces:
      enabled: true
      list:
        iterface1:
          pages: [0,2,4,6,8] #páginas en las que estarán
          slots: [0-9,44-53,17,26,35,36,27,18] #Slots en los que estarán
          item: item1 #item1 en iteminterface.yml
        iterface2:
          pages: [1,3,5,7,9]
          slots: [0-9,44-53,17,26,35,36,27,18] #Slots en los que estarán
          item: item2 #item2 en iteminterface.yml
        iterface3:
          pages: [0-8] 
          slots: [52]
          item: item3 #item3 en iteminterface.yml
        iterface4:
          pages: [1-9] #páginas en las que estarán
          slots: [51]
          item: item4 #item4 en iteminterface.yml
        iterface5:
          pages: [1-9] #páginas en las que estarán
          slots: [50]
          item: item5 #item5 en iteminterface.yml
```

## Etapas - sección

Las etapas se usan para dar estado al inventario ya sea para cambiar el título cada segundo o para cambiar el contenido de las interfaces de elementos.

### Cosas a tener en cuenta

1.  Recuerda especificar las páginas
2.  Si lo pones en refresh:0 puedes usarlo con el sistema de acciones del propio plugin
3.  Ejecutar async significa que estará bien
4.  Puedes cambiar lo que quieras, si quieres cambiar solo el título, elimina la sección de interfaces y viceversa, si quieres solo cambiar las interfaces, quita la línea del título.
5.  Ten en cuenta que esto se ejecuta de arriba hacia abajo

### YAML

```yml
.
    stages:
      refresh: 0
      list:
        stage_1:
          title: "<red>Etapa 1"
          interfaces:
            list:
              item_action:
                pages: [0-2]
                slots: [22]
                item: itemAction
              next_page:
                pages: [0-1] 
                slots: [53]
                item: item3 #item3 en iteminterface.yml
              back_page:
                pages: [1-2] #páginas en las que estarán
                slots: [52]
                item: item4 #item4 en iteminterface.yml
              search_page:
                pages: [0-2] #páginas en las que estarán
                slots: [46]
                item: item5 #item5 en iteminterface.yml
              placeholder:
                pages: [0] #páginas en las que estarán
                slots: [0-8]
                item: itemPlaceHolder #item5 en iteminterface.yml
```

## Ejemplo de configuración Yaml

<details>
<summary>Hacer clic para expandir</summary>

```yml
storages:
  storage1:
    config:
      max_views: -1
    storage:
      rows: 6
      pages: 3
      inventory_type: chest
      title: "Almacenamiento (%actual_page%/%max_pages%)"
      properties:
        isTempStorage: false
        dropAllItemsOnClose: false
    sounds:
      enabled: true
      list:
        sound_1:
          type: close
          pages: [0,1]
          sound: 'minecraft:block.barrel.close'
        sound_2:
          type: open
          pages: [0,1]
          sound: 'minecraft:block.barrel.open'
    items:
      default:
        enabled: true
        list:
          item_1:
            pages: [0]
            slots: [0]
            amount: 10-40
            chance: 40
            items: 
              - "mc:stone"
      block:
        enabled: true
        list:
          item_1:
            pages: [0]
            slots: [0]
            amount: 10-40
            chance: 40
            items: 
              - "mc:stone"
    whitelist:
      enabled: false
      list:
        whitelist_1:
          pages: [0,1]
          slots: [0]
          items: 
            - "mc:stone"
    blacklist:
      enabled: false
      list:
        blacklist_1:
          pages: [0,1]
          slots: [0]
          items: 
            - "mc:netherite_sword"
    interfaces:
      enabled: true
      list:
        iterface1:
          pages: [0,2]
          slots: [0-9,44-53,17,26,35,36,27,18]
          item: item1
        iterface2:
          pages: [1]
          slots: [0-9,44-53,17,26,35,36,27,18]
          item: item2
        iterface3:
          pages: [0-2] 
          slots: [52]
          item: item3
        iterface4:
          pages: [1-2]
          slots: [51]
          item: item4
    stages:
      refresh: 20
      list:
        stage_1:
          title: "<red>Etapa 1"
          interfaces:
            list:
              next_page:
                pages: [0-1] 
                slots: [53]
                item: item3
              back_page:
                pages: [1-2]
                slots: [52]
                item: item4
        stage_2:
          title: "<blue>Etapa 2"
          interfaces:
            list:
              next_page:
                pages: [0-1] 
                slots: [53]
                item: item3
              back_page:
                pages: [1-2]
                slots: [52]
                item: item4
```

</details>