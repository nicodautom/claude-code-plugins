---
name: c3_kpi_dashboard
description: "Orquesta e integra múltiples KPIs en un reporte ejecutivo de sprint consolidado y lo guarda en Obsidian."
---

# Escenario: Sprint KPI Dashboard

* **Intención:** "Generate the KPI dashboard for Sprint 5"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId` y `sprintId`.
* **Flujo de Acción:**
  1. Invoca secuencialmente las mediciones analíticas:
     * Llama a `c3_total_hours` para obtener el total del sprint.
     * Llama a `c3_billable_ratio` para el ratio de facturación.
     * Llama a `c3_task_delays` para listar las tareas retrasadas.
  2. Integra todos los datos en un informe estructurado.
  3. Llama a `obsidian_put_content` escribiendo el reporte en Obsidian como una nota técnica en formato de dashboard ejecutivo.
  4. Muestra el reporte final al usuario.
