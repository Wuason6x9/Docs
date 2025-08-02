---
title: Recipes
description: Aadd custom recipes
published: true
date: 2024-03-10T02:25:19.358Z
tags: 
editor: undefined
dateCreated: 2024-03-09T02:00:28.645Z
---

# Recipes Custom
<br>

It allows you to create custom recipes in a simple way.

Not only does it work for storage mechanic items, you can even put other results from other plugins other than storagemechanic, but hey, just use it for storagemechanic as there are other plugins better for that!

Configuration file loc: **/plugins/StorageMechanic/recipes/**

## Shaped

#### Yaml example

```yml
recipes:
  YourRecipeName:
    type: SHAPED
    result: "sm:backpack;1"
    ingredients:
      A: mc:leather
      B: mc:chest
    shape:
      - AAA
      - ABA
      - AAA
```

<br>

## Shapeless
#### Yaml example

```yml
recipes:
  YourRecipeName:
    type: SHAPELESS
    result: "sm:backpack;1"
    ingredients:
      - mc:diamond
      - mc:leather
```