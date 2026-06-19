---
name: c1_sprint_status
description: "Genera el reporte de estado de salud y avance del sprint activo actual."
---
# Sprint Status Review
* **Intención:** Obtener estatus y salud del sprint activo actual.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetItems` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Agrupa por estado (`statusid`).
  3. Llama a `ZohoSprints_GetSprintDetails` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  4. Calcula y presenta el avance (tareas y puntos completados vs totales, bloqueos).

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
