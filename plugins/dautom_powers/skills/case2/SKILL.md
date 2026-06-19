---
name: case2
description: "Sub-enrutador para el Caso 2: Documentation and status report generation. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario de Case 2."
---
# Caso 2: Documentation and Logs (Sub-Router)
Evalúa y delega a las sub-skills correspondientes:

| Sub-Skill | Escenario | Intención |
| :--- | :--- | :--- |
| `c2_log_task_hours` | Log Task Hours | Registrar horas en una tarea. |
| `c2_log_general_hours` | Log General Hours | Registrar horas generales en proyecto. |
| `c2_task_transition` | Task Status Transition | Cambiar estado de tarea o reasignarla. |
| `c2_create_task` | Quick Task Creation | Crear tarea en backlog o sprint. |
| `c2_add_checklist` | Add Checklists to Tasks | Agregar grupos de checklist y pasos. |
| `c2_billing_consolidation` | Billing Hours Consolidation | Reportar y consolidar horas facturables. |
| `c2_manage_logs` | Edit or Delete Logged Hours | Editar o eliminar logs de tiempo. |
| `c2_update_attributes` | Update Task Attributes | Modificar estimaciones, prioridad o asignados. |
| `c2_create_doc` | Create Project Documentation | Crear notas/especificaciones en Obsidian. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Invoca y ejecuta la skill de escenario en esta respuesta.
2. **Encadenamiento:** Si solicita múltiples acciones, ejecútalas en secuencia.
3. **Resolución:** Llama a `case0` para obtener los IDs técnicos.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
