---
name: c2_manage_logs
description: "Edita los detalles de un log de horas existente o elimina el log en Zoho Sprints, actualizando la documentación local en Obsidian."
---
# Edit or Delete Logged Hours
* **Intención:** Editar o eliminar un registro de tiempo.
* **Dependencias:** `case0` para `projectId`, `itemId`, `teamId`.
* **Acciones:**
  1. Si falta `logId`, llama a `ZohoSprints_GetItemLogHours` con:
     * `path_variables`: `teamId`, `projectId`, `itemId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
     Presenta los logs para resolver el ID.
  2. **Eliminación:** Llama a `ZohoSprints_DeleteLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="deletelogs"`, `logidarr` (ej. `"[ID]"`)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. **Edición:** Llama a `ZohoSprints_UpdateLogHours` con:
     * `path_variables`: `teamId`, `projectId`, `logId`
     * `query_params`: `action="updatelog"`, `duration` (HH:MM), `notes`, `date` (YYYY-MM-DD)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  4. Llama a `obsidian_append_content` con:
     * `query_params`: `filepath` (nota diaria), `content` (detalle)
  5. Reporta el resultado.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
