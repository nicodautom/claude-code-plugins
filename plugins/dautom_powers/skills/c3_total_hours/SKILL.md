---
name: c3_total_hours
description: "Suma y reporta el total de horas registradas en un periodo para un proyecto o sprint."
---
# Total Logged Hours Tracking
* **Intención:** Obtener total de horas registradas en un rango de fechas.
* **Dependencias:** `case0` para `projectId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0`, `logtypes="[0,1,2]"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Filtra por fechas y suma todas las duraciones.
  3. Muestra el total de horas.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
