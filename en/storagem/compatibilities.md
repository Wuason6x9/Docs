---
title: Compatibilities
description: List of supported plugins, integrations, and usage examples for StorageMechanic.
published: true
date: 2025-08-14T00:00:03.260Z
tags: 
editor: markdown
dateCreated: 2025-08-02T23:24:00.387Z
---

# **Compatibilities**

## **List of compatibilities**

### Items, blocks & furnitures

- Oraxen
- ItemsAdder
- MythicMobs
- MMOItems
- CustomItems
- ExecutableItems
- ExecutableBlocks
- MythicCrucible
- CraftEngine

Adapter use: [usage](/mechanics/adapter)

### Entities

- MythicMobs
- MythicCrucible

### Protections
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

### Others
- PlaceHolderAPI
- MiniMessage

## MythicMobs & Mythic Crucible

> Works with ModelEngine and ItemsAdder Entity's

### Skills, Usage & Args

| **Skill** | **Args** | **Usage** |
| --- | --- | --- |
| smCreate | `{id=idOfStorageConfig}` | Create storage in entity (It is advisable to use it with the onSpawn trigger) |
| smLoadDefaultItems | `{}`  | Load all default items from the storage configuration. |
| smRemove | `{drop=true}` | Removes memory and database storage. It is very important that the storage is deleted if you do not want to have junk files. (It is recommended to use it with the ~onDeath trigger)  <br>  <br>If you have "drop" set to true, when it is eliminated it will drop all its contents on the ground.  <br>  <br>default: false |
| smDrop | `{}`  | makes all the storage items fall to the ground |
| smOpen | `{}`  | Open the storage (It is very important that before opening the storage has been created previously with the smCreate skill) |
| smSave | `{}`  | save the storage in the local database (it is not necessary) that you use it unless you know what you are doing. Storage Mechanic already saves storage when the server shuts down. |
| smLoad | `{}`  | Load storage in memory (not necessary) maybe you can get some performance if you use it properly |
| smExecuteAction | `{id=idOfActionConfig}` | Executes an action from the internal Storage Mechanic action system. |
| smCollect | `{}`  | Put the item in storage |

### Triggers

| Trigger | Aliases | Usage |
| --- | --- | --- |
| ~onCloseStorage | ~onOpenS ~onOpen_Storage ~onStorageOpen ~onStorage_Open | The `~onCloseStorage` is executed when a storage is closed and no one else is using that storage. |
| ~onOpenStorage | ~onCloseS ~onClose_Storage ~onStorageClose ~onStorage_Close | The `~onOpenStorage` is executed when the storage is opened for the first time. |

### Examples

#### Example of skills with a mob

```yml
WITHER_SKELETON:
  Health: 50
  Damage: 10
  Skills:
   - smCreate{id=storage1} @Self ~onSpawn #Create a Storage in the Mob
   - smLoadDefaultItems{} @Self ~onSpawn #Works for loading defaultitems from storage.yml (Only when you open the storage and see all the pages)
   - smRemove{drop=true} @Self ~onDeath #If you want him to release all his storage
   - smDrop{} @Self ~onDamaged #Drops all charged items when hit
   - smOpen{} @Self ~onInteract #Open Storage
   - smSave{} @Self ~onDespawn #Used to save and unload the mob when the chunk is no longer loaded, to save memory.
   - smLoad{} @Self ~onLoad #Loads all items in the Storage without opening the inventory.
```

#### Example of triggers

##### Mob

```yml
stone_golem:
  Type: IRON_GOLEM
  Skills:
  - model{mid=StoneGolem;n=false;drive=true;ride=true;n=nametag} ~onSpawn
  - skill{s=stone_golem_chestopen} @trigger ~onInteract #Interacting will open the chest
  - skill{s=stone_golem_chestopen_state} @self ~onOpenStorage
  - skill{s=stone_golem_chestclose} @self ~onCloseStorage #When all the players close the chest, the following will be executed
```

#### skills

```yml
stone_golem_chestopen:
  Skills:
  - smOpen{} @self
stone_golem_chestopen_state:
  Skills:
  - setAI{ai=false} @self #The mob will be paralyzed
  - delay 1
  - DefaultState{t=idle;s=open_chest} @self #It will maintain the animation of the open chest.
  - DefaultState{t=walk;s=open_chest} @self #It will maintain the animation of the open chest.
  - delay 1
  - state{s=chest_open;li=3;lo=2} @self #It will play an animation to open the chest.
stone_golem_chestclose:
  Skills:
  - state{s=open_chest;li=3;lo=2;r=true} @self #Will remove the open chest animation
  - setAI{ai=true} @self #The mob will be able to move again
  - delay 1
  - state{s=closed_chest;li=3;lo=2} @self #It will play an animation where the chest closes.
  - delay 5
  - DefaultState{t=idle;s=idle_chest} @self #Return to your default animations
  - DefaultState{t=walk;s=walk_chest} @self #Return to your default animations
```

Example of smCollect skill

This mechanism is for the mob to pick up items from the ground.

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

`?targets{a=>0}` This will cause it to only pick items when it has an item nearby based on the trigger which is `@IIR{r=3;sort=NEAREST}`

## MiniMessage

> MiniMessage Wiki: [link](https://docs.advntr.dev/minimessage/format.html)
