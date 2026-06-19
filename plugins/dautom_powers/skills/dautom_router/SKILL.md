---
name: dautom
description: "Enrutador central de Dautom. Úsalo ante cualquier consulta general para clasificar la intención y derivar a una de las 4 skills de sub-ruteo de cada caso."
---

# Dautom Central Router

Clasifica la intención del usuario y delega la ejecución de inmediato a la skill de sub-ruteo correspondiente:

| Sub-Skill de Caso | Caso de Uso Asociado | Comando/s Directo/s |
| :--- | :--- | :--- |
| `case1` | **Case 1: Daily or status report** (Reportes diarios personales, del equipo, estatus de sprints y avance de épicas). | `/dautom:case1` |
| `case2` | **Case 2: Documentation and status report generation** (Registro y edición de horas, transiciones de estados, checklists y minutas en Obsidian). | `/dautom:case2` |
| `case3` | **Case 3: KPIs report** (Métricas de horas logueadas, meta de 70% billable, velocidad de sprint y retrasos de tareas). | `/dautom:case3` |
| `case4` | **Case 4: Ask Dautom** (Búsquedas temáticas, de minutas, de guías y referencias cruzadas en Obsidian). | `/dautom:case4` |

## ⚡ Reglas de Ejecución

1. **Autodelegación Inmediata:** Si la intención del usuario y los datos son claros, carga en memoria las directrices de la sub-skill de caso correspondiente (`case1`, `case2`, `case3` o `case4`) y ejecuta las acciones/llamadas MCP de inmediato en esta misma respuesta (sin requerir confirmaciones adicionales).
2. **Encadenamiento (Multi-Skill):** Si la solicitud abarca múltiples casos (ej. registrar horas [Caso 2] y verificar el reporte diario [Caso 1]), encadena y ejecuta las sub-skills de caso en orden lógico (ej. `case2` ➔ `case1`).
3. **Manejo de Ambivalencia (Instrucción de Respuesta al Usuario):** Si la entrada del usuario es ambigua, genérica o no permite clasificar con seguridad el caso de uso, debes responder presentando obligatoriamente un mensaje de aclaración que contenga un menú estructurado con el nombre de cada caso y una pequeña descripción de su propósito, para que el usuario entienda mejor las capacidades del agente. Debes mostrar exactamente la siguiente estructura y descripciones:
   * **[1] Daily or Status Report** (`/dautom:case1`): Obtén resúmenes de actividades diarias (propias o de tus compañeros), el estatus del sprint actual o el progreso de Épicas específicas en Zoho Sprints.
   * **[2] Documentation & Logs** (`/dautom:case2`): Registra tus horas (de tareas o generales), edita/elimina tus logs de tiempo, cambia estados de tareas, gestiona checklists o crea notas/documentos en Obsidian.
   * **[3] KPIs Analytics** (`/dautom:case3`): Analiza el cumplimiento del objetivo del 70% de horas facturables (billable target), evalúa la velocidad del equipo o detecta tareas retrasadas.
   * **[4] Ask Dautom** (`/dautom:case4`): Realiza búsquedas temáticas y consultas cruzadas en tu base de conocimientos de Obsidian para consolidar guías, minutas de reuniones, especificaciones y documentación técnica.
   * *Pregunta al usuario:* *"¿Cuál de estas áreas o casos de uso deseas ejecutar hoy?"*

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
