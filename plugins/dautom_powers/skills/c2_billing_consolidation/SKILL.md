---
name: c2_billing_consolidation
description: "Consolida las horas registradas en un proyecto durante un periodo y genera un reporte en Markdown en Obsidian."
---

# Escenario: Billing Hours Consolidation

* **Intención:** "Generate a report of all hours logged in Project Alpha during the last two weeks"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId` a partir del nombre del proyecto.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` y el `projectId` resuelto, con los siguientes parámetros requeridos:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0` (vista por fecha), `logtypes="[0,2]"` (string de array JSON para incluir logs de tareas y logs generales), `index=1`, `range=250`.
  2. Filtra y procesa los registros de horas en el rango de fechas establecido por el usuario. Suma las horas facturables y las horas totales.
  3. Genera una tabla de resumen en Markdown detallando horas por usuario y por tarea.
  4. Llama a `obsidian_put_content` pasando los parámetros requeridos:
     * `filepath` (la ruta absoluta o relativa en el vault al archivo `.md`)
     * `content` (el reporte completo en formato Markdown)
  5. Muestra la tabla resultante al usuario.
