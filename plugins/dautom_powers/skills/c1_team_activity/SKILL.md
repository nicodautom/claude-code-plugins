---
name: c1_team_activity
description: "Consulta y reporta las actividades registradas hoy por un compañero de equipo en Zoho Sprints."
---

# Escenario: Team Member Activity Check

* **Intención:** "What has [Nombre] been working on today?" / "Qué ha hecho [Nombre] hoy"
* **Dependencias:** Llama a la skill interna `case0` para mapear el nombre del compañero a su Zoho `userId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando el `teamId` de sesión, con `listviewtype=1`, `index=1`, `range=100`.
  2. Filtra la respuesta por el ID del compañero resuelto y la fecha actual.
  3. Muestra una tabla clara que liste las tareas, horas registradas y notas de los logs de tiempo del compañero hoy.
