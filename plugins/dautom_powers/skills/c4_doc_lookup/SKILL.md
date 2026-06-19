---
name: c4_doc_lookup
description: "Busca y recupera explicaciones, guías o documentación de un término o concepto en Obsidian."
---
# Concept / Documentation Lookup
* **Intención:** Buscar y leer documentación técnica sobre un concepto en Obsidian.
* **Acciones:**
  1. Llama a `obsidian_simple_search` con:
     * `query_params`: `query` (término o concepto a buscar)
  2. Llama a `obsidian_batch_get_file_contents` con:
     * `query_params`: `filepaths` (lista JSON de rutas de los mejores resultados de coincidencia, máximo 5)
  3. Extrae las definiciones clave de las notas y las presenta con enlaces clicables (`[Nombre](file:///...)`).

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
