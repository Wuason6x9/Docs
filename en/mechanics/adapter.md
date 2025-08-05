---
title: Adapter usage
description: Guide to compatibility prefixes and usage for the Adapter system.
published: true
date: 2025-08-05T00:28:54.778Z
tags: 
editor: markdown
dateCreated: 2025-08-02T23:23:41.803Z
---

# Compatibility / Prefixes

## Usage

### What is it?
It is a system to obtain items in a simple and quick implementation way!

### Syntax
`COMPATIBILITY_ID:ITEMID`

<h2>Compatibilities</h2>

<ul class="compatibility-list">
  <li>
    <a href="#itemsadder">
      <img src="https://files.techmc.es/studio/assents/others-plugins/itemsadder.jpg" class="compatibility-logo" alt="ItemsAdder">
      <em>ItemsAdder</em>
    </a>
  </li>
  <li>
    <a href="#craftengine">
      <img src="https://files.techmc.es/studio/assents/others-plugins/craftengine.png" class="compatibility-logo" alt="CraftEngine">
      <em>CraftEngine</em>
    </a>
  </li>
  <li>
    <a href="#nexo">
      <img src="https://files.techmc.es/studio/assents/others-plugins/nexo.png" class="compatibility-logo" alt="Nexo">
      <em>Nexo</em>
    </a>
  </li>
  <li>
    <a href="#mythicmobs">
      <img src="https://files.techmc.es/studio/assents/others-plugins/mythicmobs.jpg" class="compatibility-logo inverted" alt="MythicMobs">
      <em>MythicMobs</em>
    </a>
  </li>
  <li>
    <a href="#mmoitems">
      <img src="https://files.techmc.es/studio/assents/others-plugins/mmoitems.jpg" class="compatibility-logo" alt="MMOItems">
      <em>MMOItems</em>
    </a>
  </li>
  <li>
    <a href="#oraxen">
      <img src="https://files.techmc.es/studio/assents/others-plugins/oraxen.jpg" class="compatibility-logo" alt="Oraxen">
      <em>Oraxen</em>
    </a>
  </li>
  <li>
    <a href="#executable-items">
      <img src="https://files.techmc.es/studio/assents/others-plugins/executableitems.jpg" class="compatibility-logo" alt="ExecutableItems">
      <em>ExecutableItems</em>
    </a>
  </li>
  <li>
    <a href="#executable-blocks">
      <img src="https://files.techmc.es/studio/assents/others-plugins/executableblocks.jpg" class="compatibility-logo" alt="ExecutableBlocks">
      <em>ExecutableBlocks</em>
    </a>
  </li>
  <li>
    <a href="#customitems">
      <img src="https://files.techmc.es/studio/assents/others-plugins/customitems.png" class="compatibility-logo" alt="CustomItems">
      <em>CustomItems</em>
    </a>
  </li>
  <li>
    <a href="#mythiccrucible">
      <img src="https://files.techmc.es/studio/assents/others-plugins/crucible.jpg" class="compatibility-logo" alt="MythicCrucible">
      <em>MythicCrucible</em>
    </a>
  </li>
  <li>
    <a href="#storagemechanic">
      <img src="https://files.techmc.es/studio/plugins/storagemechanic/logo.png" class="compatibility-logo" alt="StorageMechanic">
      <em>StorageMechanic</em>
    </a>
  </li>
</ul>

## ItemsAdder
`ia:namespace:item_id`
Plugin: [ItemsAdder](https://www.spigotmc.org/resources/%E2%9C%A8itemsadder%E2%AD%90emotes-mobs-items-armors-hud-gui-emojis-blocks-wings-hats-liquids.73355/)

## Oraxen
`or:item_id`
Plugin: [Oraxen](https://www.spigotmc.org/resources/%E2%9C%85-10-%E2%98%84%EF%B8%8F-oraxen-%C2%BB-custom-blocks-items-and-inventories.72448/)

## Nexo
`nx:item_id`
Plugin: [Nexo](https://polymart.org/resource/nexo.6901)

## StorageMechanic
`sm:item_id`
Plugin: [StorageMechanic](https://www.spigotmc.org/resources/storage-mechanics.108436/)

## Minecraft Items
`mc:item_id`
You can use nbt also:
`mc:item_id:{nbt}`

### Another Example
**Skull example 1.20.5 ≥**
```plaintext
mc:player_head[minecraft:custom_name='{"text":"Chest","color":"gold","underlined":true,"bold":true,"italic":false}',minecraft:lore=['{"text":"Player Head ID: 60260","color":"gray","italic":false}','{"text":"www.minecraft-heads.com","color":"blue","italic":false}'],profile="LordRazen"]
```
**Skull example 1.20.5 <**
```plaintext
mc:player_head{display:{Name:'{"text":"Chest","color":"gold","underlined":true,"bold":true,"italic":false}',Lore:['{"text":"Player Head ID: 60260","color":"gray","italic":false}','{"text":"www.minecraft-heads.com","color":"blue","italic":false}']},SkullOwner:"LordRazen"}
```

## MMOItems
`mmoI:type:id(:level:tier)` the (Level:Tier) is optional, but if you place one of the two, you need to place both.
Plugin: [MMOItems](https://www.spigotmc.org/resources/mmoitems.39267/)

## MythicMobs
`mythic:item_id`
Plugin: [MythicMobs](https://mythiccraft.io/index.php?resources/mythicmobs.1/)

## MythicCrucible
`crucible:item_id`
Plugin: [MythicCrucible](https://mythiccraft.io/index.php?resources/crucible-create-unbelievable-mythic-items.2/)

## CustomItems
`cui:item_id`
Plugin: [CustomItems](https://www.spigotmc.org/resources/%E2%9B%8F-custom-items-%E2%9C%85-1-20-ready-%E2%9C%85-make-new-items-blocks-with-new-textures-recipes-events-actions.63848/)

## Executable blocks
`eb:item_id`
Plugin: [ExecutableBlocks](https://www.spigotmc.org/resources/custom-blocks-plugin-executable-blocks.93406/)

## Executable Items
`ei:item_id`
Plugin: [ExecutableItems](https://www.spigotmc.org/resources/custom-items-plugin-executable-items.77578/)

## How to add new compatibility?
Go to our discord and create a suggestion!

Discord: [https://discord.gg/2XNq7Thnqr](https://discord.gg/2XNq7Thnqr)
