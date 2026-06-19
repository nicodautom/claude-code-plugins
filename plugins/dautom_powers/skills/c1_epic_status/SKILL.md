---
name: c1_epic_status
description: "Mide y reporta el progreso, tareas y estado de salud de una Épica en Zoho Sprints."
---
# Epic Status Review
* **Intención:** Progreso y tareas de una Épica.
* **Dependencias:** `case0` para `projectId`, `epicId`, `sprintId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetEpicDetails` con:
     * `path_variables`: `teamId`, `projectId`, `epicId`
     * `query_params`: `action="data"`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Llama a `ZohoSprints_GetEpicAssociatedItems` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Procesa y presenta ratios de avance y estado de salud.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
