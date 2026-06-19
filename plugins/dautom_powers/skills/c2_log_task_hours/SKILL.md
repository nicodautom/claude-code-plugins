---
name: c2_log_task_hours
description: "Registra horas trabajadas en una tarea específica en Zoho Sprints y documenta el log en Obsidian."
---
# Log Task Hours
* **Intención:** Registrar tiempo en una tarea específica.
* **Dependencias:** `case0` para `projectId`, `sprintId`, `itemId`, `userId`, `teamId`.
* **Acciones:**
  1. Calcula fecha (`YYYY-MM-DD` basada en sistema) y duración (`HH:MM`).
  2. Llama a `ZohoSprints_AddItemLogHours` con:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `action="additemlog"`, `date`, `duration`, `users` (userId), `isbillable` (entero), `notes` (opcional)
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  3. Llama a `obsidian_append_content` con:
     * `query_params`: `filepath` (nota diaria), `content` (registro detallado)
  4. Confirma el registro.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
