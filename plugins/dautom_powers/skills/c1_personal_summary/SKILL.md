---
name: c1_personal_summary
description: "Genera el reporte diario personal cruzando Zoho Sprints y Obsidian."
---

# Escenario: Personal Daily Summary

* **Intención:** "Show me my daily status report today" / "Qué hice hoy"
* **Dependencias:** Consulta y delega de manera silenciosa en `case0` para confirmar que los IDs básicos estén cargados.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` y `userId` del contexto, con `listviewtype=1`, `logtypes="0,1,2"`, filtrado por la fecha de hoy.
  2. Llama a `obsidian_get_periodic_note` con `period="daily"` y `type="content"` para recuperar la nota diaria local.
  3. Compara y cruza la información para generar un reporte que consolide las tareas y horas de Zoho con las notas tomadas en Obsidian.
  4. Muestra la información de forma estructurada.
