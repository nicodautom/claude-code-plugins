---
name: case1
description: "Sub-enrutador para el Caso 1: Daily or status report. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 1."
---

# Caso 1: Daily or Status Report (Sub-Router)

Evalúa la intención del usuario y delega la ejecución de inmediato a una o más de las siguientes sub-skills de escenario específicas:

| Sub-Skill de Escenario | Escenario Asociado | Propósito / Intención del Usuario |
| :--- | :--- | :--- |
| `c1_personal_summary` | **Personal Daily Summary** | Obtener resumen de las actividades diarias del usuario actual en Zoho y Obsidian. |
| `c1_team_activity` | **Team Member Activity Check** | Consultar qué ha estado haciendo hoy un compañero específico del equipo. |
| `c1_sprint_status` | **Sprint Status Review** | Revisar el estado actual de completitud, tareas y salud del sprint activo. |
| `c1_recent_activity` | **Recent Activity Stream** | Ver el flujo cronológico de cambios y actualizaciones del último día. |
| `c1_epic_status` | **Epic / Deliverable Status Review** | Analizar el progreso general y estado de una Épica del proyecto. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Si la solicitud del usuario coincide con uno de los escenarios descritos, carga e invoca directamente la skill de escenario correspondiente en esta misma respuesta.
2. **Encadenamiento:** Si el usuario solicita múltiples reportes (ej. su reporte diario y también el estatus del sprint), encadena e invoca las skills necesarias de forma secuencial.
3. **Resolución de Contexto:** Las sub-skills invocadas delegarán internamente en la skill de resolución `case0` para obtener los IDs técnicos correspondientes (`projectId`, `sprintId`, `epicId` o el ID del compañero) a partir de nombres comunes.
