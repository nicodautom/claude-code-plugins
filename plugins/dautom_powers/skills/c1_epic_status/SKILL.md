---
name: c1_epic_status
description: "Mide y reporta el progreso, tareas y estado de salud de una Épica en Zoho Sprints."
---

# Escenario: Epic / Deliverable Status Review

* **Intención:** "What is the status of Epic [Nombre]?" / "Progreso de la épica"
* **Dependencias:** Llama a `case0` para obtener el `projectId` y el `epicId` de la Épica solicitada.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetEpicDetails` utilizando:
     * `path_variables`: `teamId`, `projectId`, `epicId`
     * `query_params`: `action="data"`
  2. Llama a `ZohoSprints_GetEpicAssociatedItems` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId` (usa el sprint activo obtenido en `case0`, o en su defecto un ID de sprint resuelto de la lista del proyecto)
     * `query_params`: `action="data"`, `index=1`, `range=100`
  3. Procesa y calcula los ratios de avance (tareas completadas vs pendientes y puntos de historia cerrados vs totales).
  4. Presenta el resumen analítico al usuario.
