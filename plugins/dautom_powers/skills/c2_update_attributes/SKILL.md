---
name: c2_update_attributes
description: "Modifica atributos específicos de una tarea (puntos de estimación, prioridad, asignados) en Zoho Sprints."
---
# Update Task Attributes
* **Intención:** Cambiar estimación, prioridad o asignados en tarea.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `itemId`, `teamId`.
* **Acciones:**
  1. Si cambia prioridad, llama a `ZohoSprints_GetProjectPriorities` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
     Obtén `projpriorityid`.
  2. Llama a `ZohoSprints_UpdateItem` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params` / `body` (según herramienta): `point` (puntos), `projpriorityid`, `newusers`, `delusers` (opcional)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Muestra confirmación.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
