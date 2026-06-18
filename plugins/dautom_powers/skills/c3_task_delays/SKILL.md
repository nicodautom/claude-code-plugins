---
name: c3_task_delays
description: "Detección de tareas retrasadas y desviaciones de estimación en el sprint activo."
---

# Escenario: Task Delay and Sprint Slippage

* **Intención:** "Identify any tasks in the active sprint that are currently delayed or have missed their due date"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId` y `sprintId` del Sprint Activo.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetSprintDetails` para obtener la fecha de finalización del sprint.
  2. Llama a `ZohoSprints_GetItems` con el sprint activo.
  3. Filtra las tareas no cerradas donde la fecha actual supere su fecha de entrega (`enddate`) o el fin del sprint.
  4. También identifica tareas cuyo tiempo registrado en logs de horas sea superior a los puntos de estimación iniciales.
  5. Muestra la lista de desviaciones y sus responsables.
