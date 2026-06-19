---
name: c3_billable_ratio
description: "Calcula el porcentaje de horas facturables (billable ratio) contra el target del 70%."
---
# Billable Hours Ratio
* **Intención:** Calcular ratio de horas facturables vs meta 70%.
* **Dependencias:** `case0` para `projectId`, `teamId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0`, `logtypes="[0,1,2]"`, `index=1`, `range=250`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Suma las horas facturables (`isbillable` = 1) y las horas totales.
  3. Calcula la relación (facturables/totales) y compárala con el 70%.
  4. Muestra el resultado de forma clara.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
