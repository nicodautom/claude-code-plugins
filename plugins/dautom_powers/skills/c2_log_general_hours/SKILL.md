---
name: c2_log_general_hours
description: "Registra horas dedicadas a actividades generales de un proyecto (reuniones, capacitaciones, etc.) en Zoho y documenta en Obsidian."
---

# Escenario: Log General Hours

* **Intención:** "Log 1.5 non-billable hours today for sync meeting"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId`.
* **Flujo de Acción:**
  1. Calcula la fecha actual o relativa (ej. "ayer") consultando la hora del sistema en los metadatos y formatea la fecha a `YYYY-MM-DD`. Convierte la duración al formato `HH:MM`.
  2. Llama a `ZohoSprints_AddGeneralLogHours` utilizando:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`:
       - `logtitle` (título del log, ej. "Sync meeting")
       - `duration` (duración en formato `HH:MM`, ej. "01:30")
       - `date` (fecha en formato `YYYY-MM-DD`)
       - `users` (ID del usuario, obtenido de la sesión o del contexto en `case0`)
       - `isbillable` (entero: `0` para no-facturable, `1` para facturable; mapear según la petición del usuario)
       - `notes` (opcional, descripción del log de tiempo)
  3. Llama a `obsidian_append_content` utilizando:
     * `query_params`:
       - `filepath` (la ruta absoluta o relativa en el vault al archivo `.md` de la nota diaria)
       - `content` (la línea de texto a añadir detallando las horas generales registradas)
  4. Informa al usuario que las horas generales han sido registradas.
