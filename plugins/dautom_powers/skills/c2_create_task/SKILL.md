---
name: c2_create_task
description: "Crea una nueva tarea en el backlog o en el sprint activo de un proyecto en Zoho Sprints."
---

# Escenario: Quick Task Creation

* **Intención:** "Create a High priority task in Backlog named 'Refactor DB'"
* **Dependencias:** Llama a la skill interna `case0` para resolver `projectId` y el `sprintId` (del sprint activo o del backlog).
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetProjectPriorities` utilizando:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
     Esto permite obtener los IDs técnicos de prioridad (`projpriorityid`) y mapear el valor (ej. "High", "Medium", "Low").
  2. Obtén el ID de tipo de item (`projitemtypeid`) consultando los tipos de item disponibles mediante `ZohoSprints_GetProjectDetails` utilizando:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`
  3. Llama a `ZohoSprints_CreateItem` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId` (si se especifica backlog, usa el ID correspondiente del backlog obtenido en `case0`)
     * `query_params`:
       - `name` (nombre del item/tarea)
       - `projitemtypeid` (ID del tipo de item obtenido en el paso 2, ej. "Task")
       - `projpriorityid` (ID de prioridad obtenido en el paso 1)
       - `point` (opcional, puntos de estimación)
       - `description` (opcional, descripción de la tarea)
  4. Muestra los detalles de la nueva tarea creada, incluyendo su ID generado.
