---
name: c2_manage_logs
description: "Edita los detalles de un log de horas existente o elimina el log en Zoho Sprints, actualizando la documentación local en Obsidian."
---

# Escenario: Edit or Delete Logged Hours

* **Intención:** "Delete my 2-hour log from yesterday on task #102" / "Edit my log"
* **Dependencias:** Llama a la skill interna `case0` para resolver `projectId` e `itemId`.
* **Flujo de Acción:**
  1. Si la solicitud no especifica un `logId`, llama a `ZohoSprints_GetItemLogHours` con los siguientes parámetros requeridos para recuperar la lista de logs de tiempo asociados a la tarea:
     * `path_variables`: `teamId`, `projectId`, `itemId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     Presenta los logs al usuario para que seleccione el ID.
  2. **Acción de Eliminación:** Llama a `ZohoSprints_DeleteLogHours` utilizando:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="deletelogs"`, `logidarr=[logId]` (ID del log a eliminar en formato de texto)
  3. **Acción de Edición:** Llama a `ZohoSprints_UpdateLogHours` utilizando:
     * `path_variables`: `teamId`, `projectId`, `logId`
     * `query_params`: `action="updatelog"` y los campos opcionales a modificar (`duration` en formato `HH:MM`, `notes`, `date` en formato `YYYY-MM-DD`).
  4. Llama a `obsidian_append_content` utilizando:
     * `query_params`:
       - `filepath` (la ruta absoluta o relativa en el vault al archivo `.md` de la nota diaria)
       - `content` (la línea de texto a añadir detallando la modificación o eliminación realizada)
  5. Reporta el resultado.
