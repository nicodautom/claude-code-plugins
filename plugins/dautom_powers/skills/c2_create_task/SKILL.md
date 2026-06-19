---
name: c2_create_task
description: "Crea una nueva tarea en el backlog o en el sprint activo de un proyecto en Zoho Sprints."
---
# Quick Task Creation
* **Intención:** Crear una tarea en backlog o sprint activo.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetProjectPriorities` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
     Identifica el `projpriorityid` según nombre de prioridad.
  2. Llama a `ZohoSprints_GetProjectDetails` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="details"`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
     Identifica el `projitemtypeid` (tipo de item).
  3. Llama a `ZohoSprints_CreateItem` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `name` (título), `projitemtypeid`, `projpriorityid`, `point` (opcional), `description` (opcional)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  4. Muestra detalles del item creado.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
