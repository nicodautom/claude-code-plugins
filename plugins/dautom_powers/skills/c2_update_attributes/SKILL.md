---
name: c2_update_attributes
description: "Modifica atributos específicos de una tarea (puntos de estimación, prioridad, asignados) en Zoho Sprints."
---

# Escenario: Update Task Attributes

* **Intención:** "Change the priority of task #5678 to High" / "Change estimations"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId`, `sprintId` e `itemId`, así como IDs de prioridad si aplica.
* **Flujo de Acción:**
  1. Si se modifica la prioridad, llama a `ZohoSprints_GetProjectPriorities` para obtener el `projpriorityid` correspondiente.
  2. Llama a `ZohoSprints_UpdateItem` pasando los parámetros a modificar como `point` (estimación), `projpriorityid` (prioridad), `newusers` o `delusers` (asignados).
  3. Muestra una confirmación detallando los atributos actualizados.
