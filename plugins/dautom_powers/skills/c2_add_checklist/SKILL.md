---
name: c2_add_checklist
description: "Crea grupos de checklists y asocia sub-items a una tarea en Zoho Sprints."
---

# Escenario: Add Checklists to Tasks

* **Intención:** "Add a checklist to task #1234 with steps: 'Verify logs', 'Run security scan'"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId`, `sprintId` e `itemId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_AddChecklistGroup` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `action="data"`, `clgroupname` (nombre de grupo descriptivo, ej. "Tareas de verificación")
     Obtén el `clGroupId` resultante de la respuesta.
  2. Para cada sub-item solicitado por el usuario, llama a `ZohoSprints_AddChecklist` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`, `clGroupId`
     * `query_params`: 
       - `clitemname` (el texto de la tarea/paso del checklist)
       - `ownerid` (ID de usuario asignado, por defecto el `userId` obtenido del contexto)
       - `priority` (entero: 0 para Ninguna, 1 para Baja, 2 para Media, 3 para Alta; por defecto usar 1)
       - `visibility` (entero: 0 para Público, 1 para Privado; por defecto usar 0)
  3. Muestra una confirmación del checklist agregado.
