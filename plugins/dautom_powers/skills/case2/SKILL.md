---
name: case2
description: "Sub-enrutador para el Caso 2: Documentation and status report generation. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 2."
---

# Caso 2: Documentation and Status Report Generation (Sub-Router)

Evalúa la intención del usuario y delega la ejecución de inmediato a una o más de las siguientes sub-skills de escenario específicas:

| Sub-Skill de Escenario | Escenario Asociado | Propósito / Intención del Usuario |
| :--- | :--- | :--- |
| `c2_log_task_hours` | **Log Task Hours** | Registrar horas trabajadas en una tarea específica en Zoho y Obsidian. |
| `c2_log_general_hours` | **Log General Hours** | Registrar horas dedicadas a actividades generales (reuniones, soporte, etc.). |
| `c2_task_transition` | **Task Status Transition** | Cambiar el estado de una tarea (ej. a 'In Review' o 'Closed') y opcionalmente reasignarla. |
| `c2_create_task` | **Quick Task Creation** | Crear rápidamente una nueva tarea en el backlog o sprint activo. |
| `c2_add_checklist` | **Add Checklists to Tasks** | Agregar grupos o sub-items de checklists a una tarea específica. |
| `c2_billing_consolidation` | **Billing Hours Consolidation** | Generar reportes en Markdown de horas facturables en proyectos. |
| `c2_manage_logs` | **Edit or Delete Logged Hours** | Editar descripciones/duración o eliminar registros de horas existentes. |
| `c2_update_attributes` | **Update Task Attributes** | Modificar estimaciones, prioridad u otros campos de una tarea. |
| `c2_create_doc` | **Create Project Documentation** | Crear notas técnicas o documentación en carpetas locales de Obsidian. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Si la solicitud del usuario coincide con uno de los escenarios descritos, carga e invoca directamente la skill de escenario correspondiente.
2. **Encadenamiento y Dependencias:** Si se realizan múltiples acciones documentales (ej. crear una tarea y luego agregarle checklists), encadena las ejecuciones en orden lógico.
3. **Resolución de Contexto:** Las sub-skills invocadas delegarán internamente en la skill de resolución `case0` para obtener IDs técnicos (`projectId`, `sprintId`, `itemId`, `clGroupId`, etc.).
