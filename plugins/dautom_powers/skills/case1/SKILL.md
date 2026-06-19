---
name: case1
description: "Sub-enrutador para el Caso 1: Daily or status report. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 1."
---
# Caso 1: Daily or Status Report (Sub-Router)
Evalúa y delega a las sub-skills correspondientes:

| Sub-Skill | Escenario | Intención |
| :--- | :--- | :--- |
| `c1_personal_summary` | Personal Daily Summary | Resumen diario personal. |
| `c1_team_activity` | Team Member Activity Check | Actividad de un compañero de equipo. |
| `c1_sprint_status` | Sprint Status Review | Estatus del sprint activo. |
| `c1_recent_activity` | Recent Activity Stream | Modificaciones y actualizaciones recientes. |
| `c1_epic_status` | Epic Status Review | Progreso de una Épica. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Invoca y ejecuta la skill de escenario en esta respuesta.
2. **Encadenamiento:** Si solicita varios reportes, ejecútalos en secuencia.
3. **Resolución:** Llama a `case0` para obtener los IDs técnicos.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
