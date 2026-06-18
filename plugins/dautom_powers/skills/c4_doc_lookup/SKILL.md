---
name: c4_doc_lookup
description: "Busca y recupera explicaciones, guías o documentación de un término o concepto en Obsidian."
---

# Escenario: Concept / Documentation Lookup

* **Intención:** "Search Dautom documentation for the deployment guide of the billing module"
* **Flujo de Acción:**
  1. Llama a `obsidian_simple_search` utilizando:
     * `query_params`: `query` (el concepto o término a buscar, ej. "deployment guide billing module")
  2. Llama a `obsidian_batch_get_file_contents` utilizando:
     * `query_params`: `filepaths` (una lista JSON/array de rutas absolutas de archivos con mejores puntuaciones de coincidencia, máximo 5)
  3. Sintetiza y extrae las definiciones principales de la documentación recuperada.
  4. Muestra la respuesta al usuario con enlaces clicables a los archivos correspondientes en Obsidian (`[Nombre](file:///...)`).
