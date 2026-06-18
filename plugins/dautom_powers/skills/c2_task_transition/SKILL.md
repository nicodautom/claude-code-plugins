---
name: c2_task_transition
description: "Modifica el estado de una tarea y permite reasignar la misma en Zoho Sprints."
---

# Escenario: Task Status Transition

* **Intención:** "Move task #4321 to 'In Review' and assign it to [Nombre]"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId`, `sprintId`, e `itemId`, así como el `userId` del nuevo asignado si aplica.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetItemDetails` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `action="details"`
     Esto verifica que el estado de destino sea válido dentro del flujo de estados.
  2. Llama a `ZohoSprints_UpdateItem` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params` / `body` (según se envíen en la herramienta): `statusid` (ID del nuevo estado) y opcionalmente `newusers` (IDs de los asignados) o `delusers`.
  3. (Opcional) Llama a `ZohoSprints_AddItemComment` para agregar un comentario que notifique el cambio utilizando:
     * `path_variables`: `teamId`, `projectId`, `itemId`, `moduleId` (usa `"61978000000002009"` por ser el ID predeterminado para el módulo de items en Zoho Sprints)
     * `query_params`: `action="addnotes"`, `name` (el texto del comentario, ej. "Move task #4321 to 'In Review'")
  4. Informa del cambio realizado.
