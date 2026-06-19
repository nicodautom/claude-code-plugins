---
name: c3_task_velocity
description: "Mide y calcula la velocidad del equipo basándose en tareas cerradas y puntos de historia en sprints anteriores finalizados."
---
# Task Completion Velocity
* **Intención:** Calcular velocidad del equipo basada en puntos de historia cerrados en sprints anteriores.
* **Dependencias:** `case0` para `projectId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetSprints` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `index=1`, `range=50`, `type="[3]"` (JSON-array string de sprints completados)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Para cada sprint completado, llama a `ZohoSprints_GetItems` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Filtra tareas en estado cerrado (Closed) y suma sus puntos (`point`).
  4. Presenta el promedio de velocidad del equipo.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
