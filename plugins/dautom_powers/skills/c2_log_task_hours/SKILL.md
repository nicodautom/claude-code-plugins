---
name: c2_log_task_hours
description: "Registra horas trabajadas en una tarea específica en Zoho Sprints y documenta el log en Obsidian."
---

# Escenario: Log Task Hours

* **Intención:** "Log 4 hours on task #1234 for today, notes: Completed unit testing"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId`, `sprintId` e `itemId` de la tarea.
* **Flujo de Acción:**
  1. Calcula la fecha actual o relativa (ej. "ayer") consultando la hora del sistema en los metadatos y formatea la fecha a `YYYY-MM-DD`. Convierte la duración al formato `HH:MM` (ej. 1.5h -> "01:30").
  2. Llama a `ZohoSprints_AddItemLogHours` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`:
       - `action="additemlog"`
       - `duration` (duración en formato `HH:MM`, ej. "04:00")
       - `date` (fecha formateada como `YYYY-MM-DD`)
       - `users` (ID del usuario de Zoho, obtenido en el contexto)
       - `isbillable` (entero: `1` para facturable, `0` para no-facturable; por defecto usar `1`)
       - `notes` (opcional, descripción del trabajo realizado, ej. "Completed unit testing")
  3. Llama a `obsidian_append_content` utilizando:
     * `query_params`:
       - `filepath` (la ruta absoluta o relativa en el vault al archivo `.md` de la nota diaria)
       - `content` (la línea de texto a añadir detallando las horas de tarea registradas)
  4. Confirma la acción al usuario.
