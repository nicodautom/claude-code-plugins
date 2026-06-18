---
name: c2_add_checklist
description: "Crea grupos de checklists y asocia sub-items a una tarea en Zoho Sprints."
---

# Escenario: Add Checklists to Tasks

* **Intención:** "Add a checklist to task #1234 with steps: 'Verify logs', 'Run security scan'"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId`, `sprintId` e `itemId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_AddChecklistGroup` indicando el nombre del grupo de checklist (ej. "Tareas de verificación"). Obtén el `clGroupId` resultante.
  2. Para cada sub-item solicitado por el usuario:
     * Llama a `ZohoSprints_AddChecklist` usando `clGroupId`, definiendo el nombre del sub-item y asignándolo al usuario (`ownerid` igual a `userId` del contexto).
  3. Muestra una confirmación del checklist agregado.
