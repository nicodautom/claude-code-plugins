---
name: c4_tagged_knowledge
description: "Agrupa y sintetiza toda la información de notas que comparten una misma etiqueta (#tag) en Obsidian."
---
# Consolidate Tagged Knowledge
* **Intención:** Resumir notas vinculadas a una etiqueta (#tag) específica.
* **Acciones:**
  1. Llama a `obsidian_search_by_tag` con:
     * `query_params`: `tag` (etiqueta a buscar sin '#' o comodines)
  2. Llama a `obsidian_batch_get_file_contents` con:
     * `query_params`: `filepaths` (lista JSON de rutas de los archivos encontrados con dicho tag)
  3. Consolida, resume y muestra la información organizada con enlaces clicables.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
