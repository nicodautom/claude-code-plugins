---
name: c2_update_attributes
description: "Modifica atributos específicos de una tarea (puntos de estimación, prioridad, asignados) en Zoho Sprints."
---

# Escenario: Update Task Attributes

* **Intención:** "Change the priority of task #5678 to High" / "Change estimations"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId`, `sprintId` e `itemId`, así como IDs de prioridad si aplica.
* **Flujo de Acción:**
  1. Si se modifica la prioridad, llama a `ZohoSprints_GetProjectPriorities` utilizando:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     Esto permite obtener el `projpriorityid` correspondiente.
  2. Llama a `ZohoSprints_UpdateItem` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params` / `body` (según se envíen en la herramienta): los campos a modificar, tales como `point` (puntos de estimación, entero), `projpriorityid` (ID de prioridad), `newusers` o `delusers` (ID de asignados).
  3. Muestra una confirmación detallando los atributos actualizados.
