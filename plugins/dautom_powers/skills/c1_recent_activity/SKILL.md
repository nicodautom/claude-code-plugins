---
name: c1_recent_activity
description: "Genera una línea de tiempo cronológica de las últimas modificaciones y actualizaciones realizadas en Zoho y Obsidian en el último día."
---

# Escenario: Recent Activity Stream

* **Intención:** "What were the latest updates made yesterday?" / "Flujo de actividad reciente"
* **Dependencias:** Llama a la skill interna `case0` para obtener `projectId` y `sprintId` activo.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetItems` utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`
     * `query_params`: `action="data"`, `index=1`, `range=100`
  2. Llama a `ZohoSprints_GetItemActivity` para las tareas modificadas recientemente utilizando:
     * `path_variables`: `teamId`, `projectId`, `sprintId`, `itemId`
     * `query_params`: `index=1`, `range=100`
  3. Llama a `obsidian_get_recent_changes` con `days=1` para consultar archivos modificados en el vault.
  4. Consolida y ordena de manera cronológica ambas fuentes en una línea de tiempo única y clara.
