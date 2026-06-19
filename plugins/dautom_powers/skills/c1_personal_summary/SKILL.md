---
name: c1_personal_summary
description: "Genera el reporte diario personal cruzando Zoho Sprints y Obsidian."
---
# Personal Daily Summary
* **Intención:** Obtener resumen diario personal de actividades.
* **Dependencias:** `case0` para `projectId`, `teamId`, `userId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=1`, `logtypes="[0,1,2]"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Filtra por `userId` del usuario y la fecha actual.
  3. Llama a `obsidian_get_periodic_note` con `query_params`: `period="daily"`.
  4. Cruza y muestra el reporte consolidado de Zoho y Obsidian.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
