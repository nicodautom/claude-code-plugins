---
name: c2_add_checklist
description: "Crea grupos de checklists y asocia sub-items a una tarea en Zoho Sprints."
---
# Add Checklists to Tasks
* **Intención:** Agregar grupo y sub-items de checklist a una tarea.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `itemId`, `userId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_AddChecklistGroup` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `action="addclgroup"`, `clgroupname` (nombre del grupo)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
     Obtén el `clGroupId` resultante.
  2. Para cada sub-item solicitado, llama a `ZohoSprints_AddChecklist` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`, `clGroupId`
     * `query_params`: `clitemname` (texto), `ownerid` (userId), `priority` (entero 0-3), `visibility` (entero 0-1)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Muestra confirmación.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
