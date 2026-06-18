---
name: c4_tagged_knowledge
description: "Agrupa y sintetiza toda la información de notas que comparten una misma etiqueta (#tag) en Obsidian."
---

# Escenario: Consolidate Tagged Knowledge

* **Intención:** "Give me a summary of all onboarding guidelines tagged with #onboarding"
* **Flujo de Acción:**
  1. Llama a `obsidian_search_by_tag` utilizando:
     * `query_params`: `tag` (el nombre del tag a buscar sin el símbolo '#', ej. "onboarding")
  2. Llama a `obsidian_batch_get_file_contents` utilizando:
     * `query_params`: `filepaths` (una lista JSON/array de rutas absolutas de los archivos encontrados con dicho tag)
  3. Sintetiza los datos cruzados agrupándolos por su archivo de origen.
  4. Muestra el resumen consolidado al usuario con enlaces directos.
