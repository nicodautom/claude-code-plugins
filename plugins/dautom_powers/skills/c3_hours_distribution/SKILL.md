---
name: c3_hours_distribution
description: "Calcula y presenta la distribución de esfuerzo (horas logueadas) de los usuarios entre los proyectos activos."
---

# Escenario: Project-wise Hours Distribution

* **Intención:** "Show me the distribution of hours logged per project for this quarter"
* **Dependencias:** Llama a la skill interna `case0` para obtener la lista de proyectos y sus IDs.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetProjects` para listar proyectos activos del workspace.
  2. Para cada proyecto activo de la lista, llama a `ZohoSprints_GetLogHours` utilizando los siguientes parámetros requeridos:
     * `path_variables`: `teamId`, `projectId`
     * `query_params`: `action="data"`, `listviewtype=0` (vista por fecha), `logtypes="[0,1,2]"` (string de array JSON para incluir todos los tipos de logs), `index=1`, `range=250`.
  3. Suma las horas totales registradas en cada proyecto dentro del rango de fechas.
  4. Presenta una tabla porcentual que muestre la distribución de esfuerzo del equipo entre proyectos.
