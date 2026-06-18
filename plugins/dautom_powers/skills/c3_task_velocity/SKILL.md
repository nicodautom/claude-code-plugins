---
name: c3_task_velocity
description: "Mide y calcula la velocidad del equipo basándose en tareas cerradas y puntos de historia en sprints anteriores finalizados."
---

# Escenario: Task Completion Velocity

* **Intención:** "What was the task velocity in Project Beta during the last sprint?"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetSprints` utilizando `teamId` y `projectId`, con `type="3"` (Sprints completados) y selecciona el último o últimos $N$ sprints.
  2. Para cada sprint, llama a `ZohoSprints_GetItems` para listar sus tareas.
  3. Filtra e identifica las tareas cerradas y suma sus puntos de estimación (`point`).
  4. Calcula la velocidad promedio (puntos completados por sprint) y presenta las métricas.
