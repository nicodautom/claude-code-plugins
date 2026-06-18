---
name: c3_hours_distribution
description: "Calcula y presenta la distribución de esfuerzo (horas logueadas) de los usuarios entre los proyectos activos."
---

# Escenario: Project-wise Hours Distribution

* **Intención:** "Show me the distribution of hours logged per project for this quarter"
* **Dependencias:** Llama a la skill interna `case0` para obtener la lista de proyectos y sus IDs.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetProjects` para listar proyectos activos.
  2. Llama a `ZohoSprints_GetLogHours` para cada proyecto en el periodo indicado.
  3. Suma las horas totales registradas en cada proyecto.
  4. Presenta una tabla porcentual que muestre la distribución de esfuerzo del equipo entre proyectos.
