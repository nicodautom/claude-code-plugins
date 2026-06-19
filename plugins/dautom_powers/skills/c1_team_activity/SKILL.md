---
name: c1_team_activity
description: "Consulta y reporta las actividades registradas hoy por un compañero de equipo en Zoho Sprints."
---
# Team Member Activity Check
* **Intención:** Consultar actividades registradas por un compañero específico hoy.
* **Dependencias:** `case0` para `projectId` y mapear nombre a Zoho `userId`.
* **Acciones:**
  1. Llama a `ZohoSprints_GetLogHours` con:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=1`, `logtypes="[0,1,2]"`, `index=1`, `range=100`
     * `headers`: `x-za-ui-version="v2"`, `X-convert-response="true"`
  2. Filtra por el `userId` del compañero y la fecha actual.
  3. Muestra tabla de actividades (tareas, horas, notas).

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
