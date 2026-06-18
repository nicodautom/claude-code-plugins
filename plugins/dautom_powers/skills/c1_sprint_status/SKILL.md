---
name: c1_sprint_status
description: "Genera el reporte de estado de salud y avance del sprint activo actual."
---

# Escenario: Sprint Status Review

* **Intención:** "Give me the status report of the current active sprint" / "Estatus del sprint"
* **Dependencias:** Llama a la skill interna `case0` para resolver el `projectId` y el `sprintId` activo.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetItems` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=250`
  2. Clasifica y agrupa las tareas por su estado (`statusid` que representa: To Do, In Progress, In Review, Testing, Closed).
  3. Llama a `ZohoSprints_GetSprintDetails` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`
  4. Calcula y presenta el porcentaje de avance (tareas completadas vs totales), puntos completados, y lista de tareas bloqueadas.
