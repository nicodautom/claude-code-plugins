---
name: c3_total_hours
description: "Calcula el total de horas acumuladas registradas por el equipo o usuario en un periodo de tiempo en Zoho Sprints."
---

# Escenario: Total Logged Hours Tracking

* **Intención:** "Show me the total hours logged by the team this week"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId` y el `userId` de compañeros si aplica.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` y el `projectId` resuelto, con los siguientes parámetros requeridos:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0` (vista por fecha), `logtypes="[0,1,2]"` (string de array JSON para incluir logs de tareas, reuniones y generales), `index=1`, `range=250`.
  2. Filtra la respuesta por usuario o rango de fechas si se requiere.
  3. Convierte y suma las duraciones (`HH:MM` a formato decimal).
  4. Muestra el total estructurado en una tabla de texto.
