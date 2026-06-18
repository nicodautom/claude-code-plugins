---
name: c2_log_task_hours
description: "Registra horas trabajadas en una tarea específica en Zoho Sprints y documenta el log en Obsidian."
---

# Escenario: Log Task Hours

* **Intención:** "Log 4 hours on task #1234 for today, notes: Completed unit testing"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId`, `sprintId` e `itemId` de la tarea.
* **Flujo de Acción:**
  1. Convierte la duración proporcionada al formato `HH:MM` (ej. 1.5h -> "01:30").
  2. Llama a `ZohoSprints_AddItemLogHours` utilizando `teamId`, `projectId`, `sprintId`, `itemId` y `userId` del contexto, indicando la duración, fecha (hoy por defecto) y notas.
  3. Llama a `obsidian_append_content` para añadir una línea detallando el log de horas en la nota diaria del día.
  4. Confirma la acción al usuario.
