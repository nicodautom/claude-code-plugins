---
name: c4_doc_lookup
description: "Busca y recupera explicaciones, guías o documentación de un término o concepto en Obsidian."
---

# Escenario: Concept / Documentation Lookup

* **Intención:** "Search Dautom documentation for the deployment guide of the billing module"
* **Flujo de Acción:**
  1. Llama a `obsidian_simple_search` utilizando la consulta del usuario.
  2. Llama a `obsidian_batch_get_file_contents` utilizando los archivos con mejores puntuaciones de coincidencia (máximo 5).
  3. Sintetiza y extrae las definiciones principales de la documentación recuperada.
  4. Muestra la respuesta al usuario con enlaces clicables a los archivos correspondientes en Obsidian (`[Nombre](file:///...)`).
