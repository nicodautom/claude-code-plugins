---
name: c3_task_delays
description: "Detección de tareas retrasadas y desviaciones de estimación en el sprint activo."
---
# Task Delay and Sprint Slippage
* **Intención:** Detectar tareas retrasadas o con desviación de estimación.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetSprintDetails` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Llama a `ZohoSprints_GetItems` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Filtra tareas no cerradas cuya fecha de entrega (`enddate`) o fin de sprint haya pasado.
  4. Compara el tiempo real logueado contra la estimación (`point`).
  5. Presenta la lista detallada de desviaciones.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
