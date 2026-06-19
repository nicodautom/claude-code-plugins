---
name: c2_task_transition
description: "Modifica el estado de una tarea y permite reasignar la misma en Zoho Sprints."
---
# Task Status Transition
* **Intención:** Cambiar estado o reasignar una tarea.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `itemId`, `userId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetItemDetails` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `action="details"`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Llama a `ZohoSprints_UpdateItem` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params` / `body` (según herramienta): `statusid` (nuevo estado), `newusers` o `delusers` (opcional, asignados)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. (Opcional) Llama a `ZohoSprints_AddItemComment` con:
     * `path_variables`: `teamId`, `projectId`, `itemId`, `moduleId` (usa `"61978000000002009"`)
     * `query_params`: `action="addnotes"`, `name` (comentario)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  4. Muestra la confirmación.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
