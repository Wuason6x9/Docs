---
title: Recetas
description: Agregar recetas personalizadas
published: true
date: 2024-03-10T02:25:19.358Z
tags: 
editor: undefined
dateCreated: 2024-03-09T02:00:28.645Z
---

# Recetas Personalizadas
<br>

Te permite crear recetas personalizadas de manera simple.

No solo funciona para elementos de storage mechanic, incluso puedes poner otros resultados de otros plugins diferentes a storagemechanic, ¡pero hey, solo úsalo para storagemechanic ya que hay otros plugins mejores para eso!

Ubicación del archivo de configuración: **/plugins/StorageMechanic/recipes/**

## Con Forma

#### Ejemplo Yaml

```yml
recipes:
  TuNombreDeReceta:
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

## Sin Forma
#### Ejemplo Yaml

```yml
recipes:
  TuNombreDeReceta:
    type: SHAPELESS
    result: "sm:backpack;1"
    ingredients:
      - mc:diamond
      - mc:leather
```