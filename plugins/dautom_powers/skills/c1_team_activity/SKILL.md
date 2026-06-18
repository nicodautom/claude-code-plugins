---
name: c1_team_activity
description: "Consulta y reporta las actividades registradas hoy por un compañero de equipo en Zoho Sprints."
---

# Escenario: Team Member Activity Check

* **Intención:** "What has [Nombre] been working on today?" / "Qué ha hecho [Nombre] hoy"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId` del proyecto actual (o proyectos activos) y mapear el nombre del compañero a su Zoho `userId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` de sesión y el `projectId` resuelto, con los siguientes parámetros requeridos:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=1` (vista por usuario), `logtypes="[0,1,2]"` (string de array JSON para incluir todos los tipos de logs), `index=1`, `range=100`.
  2. Filtra la respuesta por el `userId` del compañero resuelto y la fecha actual.
  3. Muestra una tabla clara que liste las tareas, horas registradas y notas de los logs de tiempo del compañero hoy.
