---
title: Uso de comandos
description: Lista de comandos del plugin StorageMechanic y sus permisos o uso.
published: true
date: 2025-08-26T18:34:48.557Z
tags: 
editor: markdown
dateCreated: 2025-08-02T23:23:55.329Z
---

# StorageMechanic — Comandos

Una referencia completa y fácil de usar para cada comando expuesto por el plugin StorageMechanic.

> Mantén esta página marcada. Usa los elementos desplegables, pestañas y tablas filtradas para ir directamente a lo que necesitas.
{.is-info}

## Leyenda

| Token | Significado | Ejemplo |
|-------|---------|---------|
| `<arg>` | Argumento requerido | `<id>` |
| `[arg]` | Argumento opcional | `[player]` |
| `{A\|B}` | Elegir exactamente uno literal | `{on|off}` |
| `...` | Una o más repeticiones | `<id>...` |
| `literal` | Escribir exactamente como se muestra | `api` |

Notas adicionales:

- Los selectores de jugador aceptan nombre de jugador o UUID a menos que se indique lo contrario.
- Los índices de página mostrados a los jugadores están basados en 1; la paginación interna de almacenamiento en código puede estar basada en 0.
- Todos los números son enteros en base‑10.

## Resumen Rápido

| Comando Base | Permiso Principal | Alias | Notas |
|--------------|--------------------|---------|-------|
| `/StorageMechanic` | `sm.command` | `sm`, `storagem` | Despachador raíz |

### Categorías de Alto Nivel

- Gestión del sistema de acciones
- Ciclo de vida de la API de almacenamiento (crear, abrir, listar, guardar/descargar, panel)
- Utilidades de depuración + diagnósticos
- GUIs de información de jugador + almacenamiento
- Distribución de elementos personalizados
- Recarga de configuración

## Referencia de Permisos (Canónica)

> Estos son los nodos exactos según se aplican en el código de registro de comandos actual. Algunos pueden diferir de la documentación anterior.
{.is-warning}

| Área | Nodo | Propósito |
|------|------|---------|
| Raíz | `sm.command` | Acceso al comando raíz (necesario para todo) |
| Acciones | `sm.command.actions` | Acceso al espacio de nombres `/sm actions` |
| Acciones | `sm.command.actions.disableActionYML` | Alternar poder de acciones (`/sm actions power`) |
| Acciones | `sm.command.actions.status` | Verificar estado de acciones |
| API | `sm.command.api` | Acceso al espacio de nombres `/sm api` |
| API | `sm.command.api.create` | Crear un almacenamiento |
| API | `sm.command.api.open` | Abrir un almacenamiento |
| API | `sm.command.api.delete` | Eliminar un almacenamiento |
| API | `sm.command.api.list` | Listar APIs de almacenamiento |
| API | `sm.command.api.exist` | Verificación de existencia |
| API | `sm.command.api.createIfNotExistAndOpen` | Crear si falta + abrir |
| API | `sm.command.api.saveAndUnload` | Guardar y descargar almacenamiento |
| API | `sm.command.api.panel` | Abrir GUI del panel de API |
| Depuración | `sm.command.debug` | Todos los subcomandos de depuración (prueba, volcados de datos, etc.) |
| Info | `sm.command.info` | Acceso al espacio de nombres `/sm info` |
| Info | `sm.command.info.players` | GUI de resumen de jugadores |
| Info | `sm.command.info.player` | GUI de jugador individual |
| Recargar | `sm.command.reload` | Recargar configuración |
| Elementos Personalizados | `sm.command.customitems.get` | Obtener elemento personalizado para uno mismo |
| Elementos Personalizados | `sm.command.customitems.give` | Dar elemento personalizado a jugadores |

> Otorga solo los nodos mínimos requeridos a los grupos de staff. Evita comodines en producción.
{.is-danger}

## Matriz de Comandos

| Comando (con raíz en `/sm`) | Resumen | Permiso | GUI |
|---------------------------|---------|------------|-----|
| `reload` | Recargar configuración | `sm.command.reload` | ❌ |
| `actions power` | Alternar estado de habilitación de acciones | `sm.command.actions.disableActionYML` | ❌ |
| `actions status` | Mostrar estado de acciones | `sm.command.actions.status` | ❌ |
| `api create <id> <storageConfigId>` | Crear API de almacenamiento | `sm.command.api.create` | ❌ |
| `api createIfNotExistAndOpen <id> <storageConfigId> <page> [player]` | Asegurar + abrir | `sm.command.api.createIfNotExistAndOpen` | ✅ |
| `api open <id> [page] [player]` | Abrir página de almacenamiento existente | `sm.command.api.open` | ✅ |
| `api delete <id>` | Eliminar API de almacenamiento | `sm.command.api.delete` | ❌ |
| `api exist <id>` | Verificar existencia | `sm.command.api.exist` | ❌ |
| `api list` | Listar IDs de API cargadas (clickeable) | `sm.command.api.list` | ❌ |
| `api saveAndUnload <id>` | Persistir + descargar | `sm.command.api.saveAndUnload` | ❌ |
| `api panel` | Panel interactivo de resumen de API | `sm.command.api.panel` | ✅ |
| `debug ...` | Diagnósticos y suite de pruebas | `sm.command.debug` | Mixto |
| `info players` | GUI de resumen de jugadores | `sm.command.info.players` | ✅ |
| `info player <player>` | GUI de almacenamientos de jugador individual | `sm.command.info.player` | ✅ |
| `customItems get <id> [amount]` | Dar elemento a uno mismo | `sm.command.customitems.get` | ❌ |
| `customItems give <players> <id> [amount]` | Dar elemento a jugadores | `sm.command.customitems.give` | ❌ |

## Uso Detallado

### Espacio de Nombres de Acciones

<details>
<summary><code>/sm actions power</code> — Alternar sistema de acciones</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm actions power` |
| Permiso | `sm.command.actions.disableActionYML` |
| Retorna | Mensaje de chat indicando nuevo estado |

Notas:
- Alterna entre estados habilitado/deshabilitado.
- Empareja con `status` para verificar.
</details>

<details>
<summary><code>/sm actions status</code> — Estado actual del sistema de acciones</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm actions status` |
| Permiso | `sm.command.actions.status` |
| Salida | "Power: true/false" |
</details>

### Ciclo de Vida de API (Con Pestañas)

=== "Crear y Gestionar"

<details>
<summary><code>/sm api create &lt;id&gt; &lt;storageConfigId&gt;</code> — Crear nueva API de almacenamiento</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api create <id> <storageConfigId>` |
| Permiso | `sm.command.api.create` |
| Validación | El ID no debe existir; configId debe ser válido |

Notas:
- Crea un nuevo almacenamiento con el ID especificado.
- Requiere una configuración de almacenamiento válida.
</details>

<details>
<summary><code>/sm api delete &lt;id&gt;</code> — Eliminar API de almacenamiento</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api delete <id>` |
| Permiso | `sm.command.api.delete` |
| Precaución | Elimina permanentemente todos los datos |

⚠️ **Advertencia**: Esta acción es irreversible. Asegúrate de tener respaldos.
</details>

=== "Abrir y Acceder"

<details>
<summary><code>/sm api open &lt;id&gt; [page] [player]</code> — Abrir almacenamiento existente</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api open <id> [page] [player]` |
| Permiso | `sm.command.api.open` |
| Por defecto | Página 0 para el ejecutor |

Notas:
- Si no se especifica jugador, abre para el ejecutor.
- La página debe estar dentro del rango válido.
</details>

<details>
<summary><code>/sm api createIfNotExistAndOpen &lt;id&gt; &lt;storageConfigId&gt; &lt;page&gt; [player]</code> — Crear si es necesario y abrir</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api createIfNotExistAndOpen <id> <storageConfigId> <page> [player]` |
| Permiso | `sm.command.api.createIfNotExistAndOpen` |
| Comportamiento | Crea si falta, luego abre |
</details>

=== "Información y Utilidades"

<details>
<summary><code>/sm api exist &lt;id&gt;</code> — Verificar si existe el almacenamiento</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api exist <id>` |
| Permiso | `sm.command.api.exist` |
| Retorna | Verdadero/falso en chat |
</details>

<details>
<summary><code>/sm api list</code> — Listar todas las APIs de almacenamiento</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api list` |
| Permiso | `sm.command.api.list` |
| Características | Enlaces clickeables para acceso rápido |
</details>

<details>
<summary><code>/sm api saveAndUnload &lt;id&gt;</code> — Guardar y descargar almacenamiento</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api saveAndUnload <id>` |
| Permiso | `sm.command.api.saveAndUnload` |
| Propósito | Liberar memoria preservando datos |
</details>

<details>
<summary><code>/sm api panel</code> — Panel de gestión de API</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm api panel` |
| Permiso | `sm.command.api.panel` |
| Tipo | GUI interactiva |
</details>

### GUIs de Información

<details>
<summary><code>/sm info players</code> — Resumen de todos los jugadores</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm info players` |
| Permiso | `sm.command.info.players` |
| Vista | Lista de jugadores con estadísticas de almacenamiento |
</details>

<details>
<summary><code>/sm info player &lt;player&gt;</code> — Información de jugador específico</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm info player <player>` |
| Permiso | `sm.command.info.player` |
| Detalles | Almacenamientos y páginas del jugador |
</details>

### Suite de Depuración

<details>
<summary><code>/sm debug</code> — Herramientas de diagnóstico</summary>

| Aspecto | Valor |
|--------|-------|
| Permiso | `sm.command.debug` |
| Uso | Solo para desarrollo/staging |
| Subcomandos | Múltiples pruebas y volcados de datos |

⚠️ **Advertencia**: Usar solo en entornos de prueba.
</details>

### Elementos Personalizados

<details>
<summary><code>/sm customItems get &lt;id&gt; [amount]</code> — Obtener elemento personalizado</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm customItems get <id> [amount]` |
| Permiso | `sm.command.customitems.get` |
| Por defecto | Cantidad = 1 |
</details>

<details>
<summary><code>/sm customItems give &lt;players&gt; &lt;id&gt; [amount]</code> — Dar elemento a jugadores</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm customItems give <players> <id> [amount]` |
| Permiso | `sm.command.customitems.give` |
| Selectores | Admite múltiples jugadores |
</details>

### Recarga de Configuración

<details>
<summary><code>/sm reload</code> — Recargar configuración del plugin</summary>

| Aspecto | Valor |
|--------|-------|
| Sintaxis | `/sm reload` |
| Permiso | `sm.command.reload` |
| Efecto | Recarga todos los archivos de configuración |
</details>

## Lista de Verificación Administrativa

- [ ] Otorgar `sm.command` al grupo de staff
- [ ] Otorgar nodos detallados requeridos (ver tabla arriba)
- [ ] Probar `/sm api create` con ID de configuración de muestra
- [ ] Abrir almacenamiento `/sm api open <id> 0`
- [ ] Validar descarga `/sm api saveAndUnload <id>`
- [ ] Confirmar que las GUIs abren (`/sm api panel`, `/sm info players`)
- [ ] Ejercitar comandos de depuración solo en staging

## Mejores Prácticas

> Convención de Nomenclatura
Usa prefijos: `player_<uuid>_<role>`, `team_<name>_main`, `region_<id>_loot` para evitar colisiones.
{.is-info}

> Planificación de Capacidad
Descarga almacenamientos inactivos con `saveAndUnload` durante bajo tráfico para recuperar memoria.
{.is-success}

> Seguridad
Nunca elimines almacenamientos (`api delete`) sin respaldos confirmados fuera del sitio.
{.is-danger}

## Solución de Problemas

### Problemas Comunes

| Problema | Síntoma | Solución |
|----------|---------|----------|
| "Almacenamiento no encontrado" | Error al abrir | Verificar con `/sm api exist <id>` |
| "Página fuera de rango" | Error al navegar | Usar `/sm api list` para verificar límites |
| GUI no abre | Sin respuesta al comando | Verificar permisos y logs del servidor |

### Comandos de Diagnóstico

1. `/sm api list` - Ver todos los almacenamientos
2. `/sm actions status` - Verificar estado del sistema
3. `/sm debug` - Herramientas de desarrollador

## Glosario

| Término | Definición |
|---------|------------|
| Storage API | Un almacenamiento gestionado por comandos con ID único |
| Storage Config | Plantilla que define comportamiento del almacenamiento |
| Page | División lógica dentro de un almacenamiento |
| Actions | Sistema interno para automatización de almacenamiento |

## Registro de Cambios (Doc)

| Versión | Notas |
|---------|-------|
| 1.0 | Documento inicial mejorado con estilo Wiki.js |

## Notas al Pie

[^1]: Algunas interacciones (Shift+Clicks) están codificadas de forma fija; siempre vuelve a probar después de las actualizaciones del plugin.

> Generado con asistencia. Por favor reporta discrepancias para que podamos refinar esta referencia.
{.is-warning}