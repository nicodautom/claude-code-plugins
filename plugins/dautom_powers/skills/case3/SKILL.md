---
name: case3
description: "Sub-enrutador para el Caso 3: KPIs report. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 3."
---
# Caso 3: KPIs Analytics (Sub-Router)
Evalúa y delega a las sub-skills correspondientes:

| Sub-Skill | Escenario | Intención |
| :--- | :--- | :--- |
| `c3_total_hours` | Total Logged Hours Tracking | Total de horas en proyecto o sprint. |
| `c3_billable_ratio` | Billable Hours Ratio | Ratio de horas facturables vs meta 70%. |
| `c3_task_velocity` | Task Completion Velocity | Puntos e items cerrados en sprints previos. |
| `c3_task_delays` | Task Delay and Slippage | Tareas retrasadas o fuera de fecha. |
| `c3_hours_distribution` | Hours Distribution | Distribución de horas por proyecto y tipo. |
| `c3_kpi_dashboard` | Sprint KPI Dashboard | Dashboard consolidado de KPIs. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Invoca y ejecuta la skill de escenario en esta respuesta.
2. **Encadenamiento:** Ejecuta en secuencia si se solicitan múltiples analíticas.
3. **Resolución:** Llama a `case0` para obtener los IDs técnicos.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
