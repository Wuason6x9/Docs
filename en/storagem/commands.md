---
title: Commands usage
description: List of StorageMechanic plugin commands and their permissions or usage.
published: true
date: 2024-03-05T10:40:51.689Z
tags: 
editor: markdown
dateCreated: 2023-10-01T16:45:40.629Z
---

# Commands

## List of commands

| **Commands** | **Usage / Permission** |
|--------------|-----------------------|
| /sm reload | Restart the plugin (sm.command) |
| /sm debug | It will only be useful if you are a developer or have an idea of what each command does. (sm.command.debug) |
| /sm customblocks get <id> <amount> | It is used to give you a custom block/item (sm.command.customblocks.get) |
| /sm customblocks give <player> <id> <amount> | Used to give someone a custom block/item (sm.command.customblocks.give) |
| /sm api create <id> <StorageConfigId> | Used to create storage (sm.command.api.create) |
| /sm api createIfNotExistAndOpen <id> <StorageConfigId> <page> <player / OPTIONAL> | It is used to create a storage if it does not exist with that id and open it (sm.command.api.createIfNotExistAndOpen) |
| /sm api delete <id> | Used to eliminate storage (sm.command.api.delete) |
| /sm api exist <id> | It is used to see if the storage exists (sm.command.api.exist) |
| /sm api list | It is used to see the list of storages loaded in memory. (sm.command.api.list) |
| /sm api open <id> <player / OPTIONAL> | It is used to open a storage whenever it exists. (sm.command.api.open) |
| /sm api saveAndUnload <id> | Used to save storage locally/database (sm.command.api.saveAndUnload) |
| /sm actions power | This command is used to turn StorageMechanic action events on or off. (sm.command.actions.power) |
| /sm actions status | This command is used to view the status of the actions system. (sm.command.actions.status) |
| /sm info players | A menu will open with the current connected players and you will be able to see how much storage these users have and their information in a GUI. (sm.command.info.players) |
| /sm info player <player> | It is the same as the players but this is for a specific player and you can even see the information if the player is offline. (sm.command.info.player) |
