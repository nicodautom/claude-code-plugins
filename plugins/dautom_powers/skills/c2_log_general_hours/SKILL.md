---
name: c2_log_general_hours
description: "Registra horas dedicadas a actividades generales de un proyecto (reuniones, capacitaciones, etc.) en Zoho y documenta en Obsidian."
---

# Escenario: Log General Hours

* **Intención:** "Log 1.5 non-billable hours today for sync meeting"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId`.
* **Flujo de Acción:**
  1. Convierte la duración al formato `HH:MM`.
  2. Llama a `ZohoSprints_AddGeneralLogHours` utilizando `teamId`, `projectId` y `userId` del contexto, con la duración, fecha, título del log, notas y estado billable (`isbillable=1` o `0`).
  3. Llama a `obsidian_append_content` para documentar la actividad en la nota diaria del día.
  4. Informa al usuario que las horas generales han sido registradas.
