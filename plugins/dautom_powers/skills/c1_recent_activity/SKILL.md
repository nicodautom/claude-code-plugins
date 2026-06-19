---
name: c1_recent_activity
description: "Genera una línea de tiempo cronológica de las últimas modificaciones y actualizaciones realizadas en Zoho y Obsidian en el último día."
---
# Recent Activity Stream
* **Intención:** Consultar las últimas actualizaciones en Zoho y Obsidian.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetItems` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Llama a `ZohoSprints_GetItemActivity` para las tareas modificadas con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Llama a `obsidian_get_recent_changes` (sin parámetros).
  4. Muestra una línea de tiempo cronológica consolidada.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
