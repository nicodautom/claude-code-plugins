---
name: c3_hours_distribution
description: "Analiza la distribución de horas registradas por proyecto y tipo de log (tarea vs general)."
---
# Hours Distribution
* **Intención:** Distribución de horas registradas.
* **Dependencias:** `case0` para `projectId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0`, `logtypes="[0,2]"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Clasifica y agrupa las horas registradas por tipo de log y por usuario.
  3. Presenta el resumen analítico.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
