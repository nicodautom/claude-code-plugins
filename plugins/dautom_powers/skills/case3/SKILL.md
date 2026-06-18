---
name: case3
description: "Sub-enrutador para el Caso 3: KPIs report. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 3."
---

# Caso 3: KPIs Report (Sub-Router)

Evalúa la intención del usuario y delega la ejecución de inmediato a una o más de las siguientes sub-skills de escenario específicas:

| Sub-Skill de Escenario | Escenario Asociado | Propósito / Intención del Usuario |
| :--- | :--- | :--- |
| `c3_total_hours` | **Total Logged Hours Tracking** | Calcular y mostrar el acumulado total de horas logueadas en un periodo. |
| `c3_billable_ratio` | **Billable Hours Ratio (70% Target)** | Evaluar si las horas del usuario cumplen con el objetivo del 70% facturable. |
| `c3_task_velocity` | **Task Completion Velocity** | Medir la velocidad del equipo en base a puntos de historia y tareas cerradas. |
| `c3_task_delays` | **Task Delay and Sprint Slippage** | Identificar tareas que presentan retrasos respecto a su vencimiento o estimación. |
| `c3_hours_distribution` | **Project-wise Hours Distribution** | Ver la distribución porcentual de esfuerzo del equipo entre proyectos activos. |
| `c3_kpi_dashboard` | **Sprint KPI Dashboard** | Generar un reporte consolidado con múltiples métricas clave del sprint actual. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Si la solicitud del usuario coincide con uno de los escenarios analíticos descritos, carga e invoca directamente la skill de escenario correspondiente.
2. **Encadenamiento y Dashboards:** Para reportes complejos como el Dashboard de Sprint, la skill `c3_kpi_dashboard` podrá coordinar la obtención de datos llamando a `c3_total_hours`, `c3_billable_ratio`, y `c3_task_delays` consecutivamente.
3. **Resolución de Contexto:** Las sub-skills invocadas delegarán internamente en la skill de resolución `case0` para obtener IDs técnicos (`projectId`, `sprintId`, etc.).
