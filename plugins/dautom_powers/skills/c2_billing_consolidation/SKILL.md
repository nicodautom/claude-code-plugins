---
name: c2_billing_consolidation
description: "Consolida las horas registradas en un proyecto durante un periodo y genera un reporte en Markdown en Obsidian."
---
# Billing Hours Consolidation
* **Intención:** Reporte consolidado de horas registradas en un periodo.
* **Dependencias:** `case0` para `projectId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0`, `logtypes="[0,2]"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Filtra por rango de fechas, suma horas facturables y totales.
  3. Llama a `obsidian_put_content` con:
     * `query_params`: `filepath` (nota de destino), `content` (reporte estructurado)
  4. Muestra confirmación y tabla resultante.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
