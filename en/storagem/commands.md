---
title: Commands usage
description: List of StorageMechanic plugin commands and their permissions or usage.
published: true
date: 2025-08-26T18:34:48.557Z
tags: 
editor: markdown
dateCreated: 2025-08-02T23:23:55.329Z
---

# StorageMechanic — Commands

A comprehensive, human‑friendly reference for every command exposed by the StorageMechanic plugin.

> Keep this page bookmarked. Use the collapsibles, tabs and filtered tables to jump straight to what you need.
{.is-info}

## Legend

| Token | Meaning | Example |
|-------|---------|---------|
| `<arg>` | Required argument | `<id>` |
| `[arg]` | Optional argument | `[player]` |
| `{A\|B}` | Choose exactly one literal | `{on|off}` |
| `...` | One or more repetitions | `<id>...` |
| `literal` | Type exactly as shown | `api` |

Additional notes:

- Player selectors accept player name or UUID unless stated otherwise.
- Page indexes shown to players are 1-based; internal storage paging in code may be 0-based.
- All numbers are base‑10 integers.

## Quick Overview

| Base Command | Primary Permission | Aliases | Notes |
|--------------|--------------------|---------|-------|
| `/StorageMechanic` | `sm.command` | `sm`, `storagem` | Root dispatcher |

### High-Level Categories

- Actions system management
- Storage API lifecycle (create, open, list, save/unload, panel)
- Debug + diagnostics utilities
- Player + storage information GUIs
- Custom items distribution
- Configuration reload

## Permissions Reference (Canonical)

> These are the exact nodes as enforced in the current command registration code. Some may differ from previous documentation.
{.is-warning}

| Area | Node | Purpose |
|------|------|---------|
| Root | `sm.command` | Access to root command (needed for everything) |
| Actions | `sm.command.actions` | Access to `/sm actions` namespace |
| Actions | `sm.command.actions.disableActionYML` | Toggle actions power (`/sm actions power`) |
| Actions | `sm.command.actions.status` | Check actions status |
| API | `sm.command.api` | Access to `/sm api` namespace |
| API | `sm.command.api.create` | Create a storage |
| API | `sm.command.api.open` | Open a storage |
| API | `sm.command.api.delete` | Delete a storage |
| API | `sm.command.api.list` | List storage APIs |
| API | `sm.command.api.exist` | Existence check |
| API | `sm.command.api.createIfNotExistAndOpen` | Create if missing + open |
| API | `sm.command.api.saveAndUnload` | Save & unload storage |
| API | `sm.command.api.panel` | Open API panel GUI |
| Debug | `sm.command.debug` | All debug subcommands (test, data dumps, etc.) |
| Info | `sm.command.info` | Access to `/sm info` namespace |
| Info | `sm.command.info.players` | Players overview GUI |
| Info | `sm.command.info.player` | Single player GUI |
| Reload | `sm.command.reload` | Reload configuration |
| Custom Items | `sm.command.customitems.get` | Self obtain custom item |
| Custom Items | `sm.command.customitems.give` | Give custom item to players |

> Grant only the minimal nodes required to staff groups. Avoid wildcards in production.
{.is-danger}

## Command Matrix

| Command (rooted at `/sm`) | Summary | Permission | GUI |
|---------------------------|---------|------------|-----|
| `reload` | Reload configuration | `sm.command.reload` | ❌ |
| `actions power` | Toggle actions enable state | `sm.command.actions.disableActionYML` | ❌ |
| `actions status` | Show actions state | `sm.command.actions.status` | ❌ |
| `api create <id> <storageConfigId>` | Create storage API | `sm.command.api.create` | ❌ |
| `api createIfNotExistAndOpen <id> <storageConfigId> <page> [player]` | Ensure + open | `sm.command.api.createIfNotExistAndOpen` | ✅ |
| `api open <id> [page] [player]` | Open existing storage page | `sm.command.api.open` | ✅ |
| `api delete <id>` | Delete storage API | `sm.command.api.delete` | ❌ |
| `api exist <id>` | Check existence | `sm.command.api.exist` | ❌ |
| `api list` | List loaded API IDs (clickable) | `sm.command.api.list` | ❌ |
| `api saveAndUnload <id>` | Persist + unload | `sm.command.api.saveAndUnload` | ❌ |
| `api panel` | Interactive API overview panel | `sm.command.api.panel` | ✅ |
| `debug ...` | Diagnostics & test suite | `sm.command.debug` | Mixed |
| `info players` | Players overview GUI | `sm.command.info.players` | ✅ |
| `info player <player>` | Single player storages GUI | `sm.command.info.player` | ✅ |
| `customItems get <id> [amount]` | Give item to self | `sm.command.customitems.get` | ❌ |
| `customItems give <players> <id> [amount]` | Give item to players | `sm.command.customitems.give` | ❌ |

> Page argument for `/sm api open` in code: required `page` integer followed by optional `player`. Some earlier docs omit page; ensure you supply the correct page number (0-based internally, user typically thinks 1-based). If unsure, start with `0`.
{.is-info}

## Detailed Usage

### Actions Namespace

<details>
<summary><code>/sm actions power</code> — Toggle action system</summary>

| Aspect | Value |
|--------|-------|
| Syntax | `/sm actions power` |
| Permission | `sm.command.actions.disableActionYML` |
| Returns | Chat message indicating new state |

Notes:
- Flips between enabled/disabled states.
- Pair with `status` to verify.
</details>

<details>
<summary><code>/sm actions status</code> — Current action system state</summary>

| Aspect | Value |
|--------|-------|
| Syntax | `/sm actions status` |
| Permission | `sm.command.actions.status` |
| Output | "Power: true/false" |
</details>

### API Lifecycle (Tabbed)

#### API Operations {.tabset}

##### Create
`/sm api create <id> <storageConfigId>`

- Fails if `<id>` already exists.
- Use descriptive IDs (e.g. `player_<uuid>_main`).

##### Open
`/sm api open <id> <page> [player]`

- Opens page (0-based) for target player or sender.
- Ensure storage exists.

##### Create If Missing & Open
`/sm api createIfNotExistAndOpen <id> <storageConfigId> <page> [player]`

- Atomic convenience: create only if absent.
- Will open even if already present.

##### Delete
`/sm api delete <id>`

- Irreversible (unless you have backups).

##### Exist
`/sm api exist <id>`

- Returns boolean message.

##### List
`/sm api list`

- Displays clickable colored IDs.

##### Save & Unload
`/sm api saveAndUnload <id>`

- Persists to backend then frees memory.
- Re-load occurs implicitly on next open/create call.

##### Panel (GUI)
`/sm api panel`

- Interactive management interface:
  - View loaded state
  - Inspect page counts, viewers
  - Shift+Right Click to remove
  - Shift+Left Click to refresh highlight

### Info GUIs

| Command | Purpose | Interactions |
|---------|---------|--------------|
| `/sm info players` | Overview of online players with storage stats | Click player -> loads their storages pane |
| `/sm info player <player>` | Directly open a player's storage list | Left = open storage; Right = save (if loaded); Shift+Right = wipe contents |

> Action mappings depend on shift + mouse button logic present in the GUI handlers.
{.is-info}

### Debug Suite

All under: `/sm debug` (permission `sm.command.debug`).

Subcommands (subject to change):

- `test` — Opens an anvil-based searchable item list (ItemsAdder integration) for testing.
- `ActiveHopperHashMap` — Dumps hopper activity maps.
- `getActiveBlockStorages` — Lists currently active block storages.
- `saveAllData` — Async save of all data managers.
- `enable` / `disable` — Toggle per-player debug mode.
- `open <page> <ID>` — Force-open an internal storage by raw ID.
- `deleteTrash` — Purge trash system.

> Use only in controlled environments; may expose internal identifiers or large dumps.
{.is-warning}

### Custom Items

#### Get for Self
`/sm customItems get <id> [amount]`

- Amount defaults to 1 (clamped 1–64). Invalid values fall back to 64.
- Adds to inventory or drops if full.

#### Give to Players
`/sm customItems give <players> <id> [amount]`

- `<players>` supports multiple selections (space-separated) or selector logic depending on the command API implementation.
- Performs same amount validation as self-get.

### Configuration Reload

`/sm reload`

- Reloads configuration files (language, storage config, etc.).
- May introduce brief performance hitches; avoid spamming.

## Administrative Checklist

- [ ] Grant `sm.command` to staff group
- [ ] Grant required fine-grained nodes (see table above)
- [ ] Test `/sm api create` with sample config ID
- [ ] Open storage `/sm api open <id> 0`
- [ ] Validate unloading `/sm api saveAndUnload <id>`
- [ ] Confirm GUIs open (`/sm api panel`, `/sm info players`)
- [ ] Exercise debug commands on staging only

## Best Practices

> Naming Convention
Use prefixes: `player_<uuid>_<role>`, `team_<name>_main`, `region_<id>_loot` to avoid collisions.
{.is-info}

> Capacity Planning
Unload inactive storages with `saveAndUnload` during low traffic to reclaim memory.
{.is-success}

> Safety
Never delete storages (`api delete`) without confirmed off-site backups.
{.is-danger}

## Troubleshooting

| Symptom | Likely Cause | Resolution |
|---------|--------------|------------|
| "You do not have permission" | Missing node | Add specific permission via LuckPerms or equivalent |
| Open command does nothing | Storage not loaded / wrong page number | Verify existence, use page `0` first |
| Invalid ID on custom item | Mis-typed or not registered in config | Check `CustomItems/` YAML and reload |
| Page out of range | Using 1-based when command expects 0-based | Subtract 1 from the page you intend |
| Data not saving | Missed save/unload cycle | Run `saveAllData` (debug) or `saveAndUnload` per storage |

## Glossary

| Term | Definition |
|------|------------|
| Storage API | Manager object binding an ID to a storage instance and config |
| Storage Config | Template defining pages, layout, behavior for new storages |
| Viewer | Player currently with a storage GUI open |
| Unloaded Storage | Persisted data not currently resident in memory |

## Change Log (Doc)

| Version | Notes |
|---------|-------|
| 1.0 | Initial enhanced Wiki.js styled document |

## Footnotes

[^1]: Some interactions (Shift+Clicks) are hard-coded; always re-test after plugin updates.

> Generated with assistance. Please report discrepancies so we can refine this reference.
{.is-warning}

