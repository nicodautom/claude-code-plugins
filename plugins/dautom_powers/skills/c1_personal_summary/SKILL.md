---
name: c1_personal_summary
description: "Genera el reporte diario personal cruzando Zoho Sprints y Obsidian."
---

# Escenario: Personal Daily Summary

* **Intención:** "Show me my daily status report today" / "Qué hice hoy"
* **Dependencias:** Consulta y delega de manera silenciosa en `case0` para obtener el `projectId` del proyecto actual (o proyectos activos) y asegurar que el `teamId` y `userId` estén cargados.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` y el `projectId` resuelto, con los siguientes parámetros requeridos:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=1` (vista por usuario), `logtypes="[0,1,2]"` (string de array JSON que incluye logs de item, meeting y general), `index=1`, `range=100`.
  2. Filtra los logs devueltos por el `userId` del usuario de sesión y la fecha de hoy.
  3. Llama a `obsidian_get_periodic_note` con `period="daily"` y `type="content"` para recuperar la nota diaria local.
  4. Compara y cruza la información para generar un reporte que consolide las tareas y horas de Zoho con las notas tomadas en Obsidian.
  5. Muestra la información de forma estructurada.
