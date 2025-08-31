---
title: Compatibilidades
description: Lista de plugins compatibles, integraciones y ejemplos de uso para StorageMechanic.
published: true
date: 2025-08-14T00:00:03.260Z
tags: 
editor: markdown
dateCreated: 2025-08-02T23:24:00.387Z
---

# **Compatibilidades**

## **Lista de compatibilidades**

### Elementos, bloques y muebles

- Oraxen
- ItemsAdder
- MythicMobs
- MMOItems
- CustomItems
- ExecutableItems
- ExecutableBlocks
- MythicCrucible
- CraftEngine

Uso del adaptador: [uso](/mechanics/adapter)

### Entidades

- MythicMobs
- MythicCrucible

### Protecciones
  - BentoBox
  - CrashClaim
  - Dominion
  - FabledSkyBlock
  - FactionsUUID
  - GriefDefender
  - GriefPrevention
  - hClaims
  - HuskClaims
  - HuskTowns
  - IridiumSkyBlock
  - KingdomsX
  - Landlord
  - Lands
  - PlotSquared
  - PreciousStones
  - ProtectionStones
  - RedProtect
  - Residence
  - SaberFactions
  - SuperiorSkyBlock
  - Towny
  - UltimateClaims
  - UltimateClans
  - WorldGuard
  - XClaim

### Otros
- PlaceHolderAPI
- MiniMessage

## MythicMobs & Mythic Crucible

> Funciona con ModelEngine y Entidades de ItemsAdder

### Habilidades, Uso y Argumentos

| **Habilidad** | **Args** | **Uso** |
| --- | --- | --- |
| smCreate | `{id=idOfStorageConfig}` | Crear almacenamiento en entidad (Es recomendable usarlo con el trigger onSpawn) |
| smLoadDefaultItems | `{}`  | Cargar todos los elementos por defecto de la configuración de almacenamiento. |
| smRemove | `{drop=true}` | Elimina el almacenamiento de memoria y base de datos. Es muy importante que el almacenamiento sea eliminado si no quieres tener archivos basura. (Se recomienda usarlo con el trigger ~onDeath)  <br>  <br>Si tienes "drop" configurado como true, cuando sea eliminado tirará todo su contenido al suelo.  <br>  <br>por defecto: false |
| smDrop | `{}`  | hace que todos los elementos del almacenamiento caigan al suelo |
| smOpen | `{}`  | Abrir el almacenamiento (Es muy importante que antes de abrir el almacenamiento haya sido creado previamente con la habilidad smCreate) |
| smSave | `{}`  | guardar el almacenamiento en la base de datos local (no es necesario) que lo uses a menos que sepas lo que estás haciendo. Storage Mechanic ya guarda el almacenamiento cuando el servidor se apaga. |
| smLoad | `{}`  | Cargar almacenamiento en memoria (no necesario) quizás puedas obtener algo de rendimiento si lo usas apropiadamente |
| smExecuteAction | `{id=idOfActionConfig}` | Ejecuta una acción del sistema interno de acciones de Storage Mechanic. |
| smCollect | `{}`  | Poner el elemento en el almacenamiento |

### Triggers

| Trigger | Alias | Uso |
| --- | --- | --- |
| ~onCloseStorage | ~onOpenS ~onOpen_Storage ~onStorageOpen ~onStorage_Open | El `~onCloseStorage` se ejecuta cuando un almacenamiento se cierra y nadie más está usando ese almacenamiento. |
| ~onOpenStorage | ~onCloseS ~onClose_Storage ~onStorageClose ~onStorage_Close | El `~onOpenStorage` se ejecuta cuando el almacenamiento se abre por primera vez. |

### Ejemplos

#### Ejemplo de habilidades con un mob

```yml
WITHER_SKELETON:
  Health: 50
  Damage: 10
  Skills:
   - smCreate{id=storage1} @Self ~onSpawn #Crear un Almacenamiento en el Mob
   - smLoadDefaultItems{} @Self ~onSpawn #Funciona para cargar elementos por defecto desde storage.yml (Solo cuando abres el almacenamiento y ves todas las páginas)
   - smRemove{drop=true} @Self ~onDeath #Si quieres que libere todo su almacenamiento
   - smDrop{} @Self ~onDamaged #Tira todos los elementos cargados cuando es golpeado
   - smOpen{} @Self ~onInteract #Abrir Almacenamiento
   - smSave{} @Self ~onDespawn #Usado para guardar y descargar el mob cuando el chunk ya no está cargado, para ahorrar memoria.
   - smLoad{} @Self ~onLoad #Carga todos los elementos en el Almacenamiento sin abrir el inventario.
```

#### Ejemplo de triggers

##### Mob

```yml
stone_golem:
  Type: IRON_GOLEM
  Skills:
  - model{mid=StoneGolem;n=false;drive=true;ride=true;n=nametag} ~onSpawn
  - skill{s=stone_golem_chestopen} @trigger ~onInteract #Interactuar abrirá el cofre
  - skill{s=stone_golem_chestopen_state} @self ~onOpenStorage
  - skill{s=stone_golem_chestclose} @self ~onCloseStorage #Cuando todos los jugadores cierren el cofre, se ejecutará lo siguiente
```

#### habilidades

```yml
stone_golem_chestopen:
  Skills:
  - smOpen{} @self
stone_golem_chestopen_state:
  Skills:
  - setAI{ai=false} @self #El mob estará paralizado
  - delay 1
  - DefaultState{t=idle;s=open_chest} @self #Mantendrá la animación del cofre abierto.
  - DefaultState{t=walk;s=open_chest} @self #Mantendrá la animación del cofre abierto.
  - delay 1
  - state{s=chest_open;li=3;lo=2} @self #Reproducirá una animación para abrir el cofre.
stone_golem_chestclose:
  Skills:
  - state{s=open_chest;li=3;lo=2;r=true} @self #Eliminará la animación del cofre abierto
  - setAI{ai=true} @self #El mob podrá moverse de nuevo
  - delay 1
  - state{s=closed_chest;li=3;lo=2} @self #Reproducirá una animación donde el cofre se cierra.
  - delay 5
  - DefaultState{t=idle;s=idle_chest} @self #Volver a sus animaciones por defecto
  - DefaultState{t=walk;s=walk_chest} @self #Volver a sus animaciones por defecto
```

Ejemplo de habilidad smCollect

Este mecanismo es para que el mob recoja elementos del suelo.

```yml
.
  - skill{s=[
      - setAI{ai=false} @self ?targets{a=>0}
      - delay 2
      - state{s=swallow_item;li=3;lo=2} @self ?targets{a=>0}
      - delay 12
      - SmCollect{} @IIR{r=3;sort=NEAREST} ?targets{a=>0}
      - delay 15
      - SmCollect{} @IIR{r=3;sort=NEAREST} ?targets{a=>0}
      - delay 10
      - setAI{ai=true} @self ?targets{a=>0}
    ]} @IIR{r=3;sort=NEAREST} ~onTimer:40
```

`?targets{a=>0}` Esto hará que solo recoja elementos cuando tenga un elemento cerca basado en el trigger que es `@IIR{r=3;sort=NEAREST}`

## MiniMessage

> MiniMessage Wiki: [enlace](https://docs.advntr.dev/minimessage/format.html)