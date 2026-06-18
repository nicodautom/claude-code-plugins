---
name: c2_create_task
description: "Crea una nueva tarea en el backlog o en el sprint activo de un proyecto en Zoho Sprints."
---

# Escenario: Quick Task Creation

* **Intención:** "Create a High priority task in Backlog named 'Refactor DB'"
* **Dependencias:** Llama a la skill interna `case0` para resolver `projectId` y el `sprintId` (del sprint activo o del backlog).
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetProjectPriorities` para obtener los IDs técnicos de prioridad y mapear el valor (ej. "High", "Medium", "Low").
  2. Llama a `ZohoSprints_CreateItem` utilizando `teamId`, `projectId`, `sprintId`, indicando el nombre de la tarea, ID de prioridad, tipo de item (por defecto Task/Story) y puntos de estimación si se proveen.
  3. Muestra los detalles de la nueva tarea creada, incluyendo su ID generado.
