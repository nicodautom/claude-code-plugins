---
name: c2_manage_logs
description: "Edita los detalles de un log de horas existente o elimina el log en Zoho Sprints, actualizando la documentación local en Obsidian."
---

# Escenario: Edit or Delete Logged Hours

* **Intención:** "Delete my 2-hour log from yesterday on task #102" / "Edit my log"
* **Dependencias:** Llama a la skill interna `case0` para resolver `projectId` e `itemId`.
* **Flujo de Acción:**
  1. Si la solicitud no especifica un `logId`, llama a `ZohoSprints_GetItemLogHours` para recuperar la lista de logs de tiempo asociados a la tarea y presentarlos al usuario para que seleccione el ID.
  2. **Acción de Eliminación:** Llama a `ZohoSprints_DeleteLogHours` utilizando `teamId`, `projectId` y el ID del log (`logidarr=[logId]`).
  3. **Acción de Edición:** Llama a `ZohoSprints_UpdateLogHours` enviando la nueva duración, notas o fecha según corresponda.
  4. Llama a `obsidian_append_content` para documentar la modificación en la nota diaria del usuario.
  5. Reporta el resultado.
