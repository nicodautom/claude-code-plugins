---
name: c2_billing_consolidation
description: "Consolida las horas registradas en un proyecto durante un periodo y genera un reporte en Markdown en Obsidian."
---

# Escenario: Billing Hours Consolidation

* **Intención:** "Generate a report of all hours logged in Project Alpha during the last two weeks"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` y `projectId`, con `listviewtype=0` (vista por fecha), rango de fechas y filtro de logs.
  2. Filtra y procesa los registros de horas en el rango establecido. Suma las horas facturables y las horas totales.
  3. Genera una tabla de resumen en Markdown detallando horas por usuario y por tarea.
  4. Llama a `obsidian_put_content` escribiendo el reporte en la ruta y archivo `.md` solicitados.
  5. Muestra la tabla resultante al usuario.
