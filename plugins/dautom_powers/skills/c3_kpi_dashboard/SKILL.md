---
name: c3_kpi_dashboard
description: "Orquesta e integra múltiples KPIs en un reporte ejecutivo de sprint consolidado y lo guarda en Obsidian."
---
# Sprint KPI Dashboard
* **Intención:** Generar un dashboard ejecutivo consolidado de KPIs.
* **Dependencias:** `case0` para `projectId`, `sprintId`.
* **Acciones:**
  1. Ejecuta analíticas de forma secuencial: `c3_total_hours`, `c3_billable_ratio` y `c3_task_delays`.
  2. Integra los resultados en un reporte Markdown unificado.
  3. Llama a `obsidian_put_content` con:
     * `query_params`: `filepath` (nota de destino del dashboard), `content` (reporte Markdown consolidado).
  4. Muestra el dashboard ejecutivo al usuario.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
