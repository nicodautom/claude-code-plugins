---
name: c4_meeting_minutes
description: "Busca y resume actas de reuniones o compromisos de un cliente en el vault de Obsidian."
---

# Escenario: Retrieve Meeting Minutes

* **Intención:** "Find the minutes of the kick-off meeting with Client X"
* **Flujo de Acción:**
  1. Llama a `obsidian_complex_search` utilizando:
     * `query_params`: `query` (un objeto JsonLogic estructurado para filtrar por tipo de archivo, contenido y ruta, ej. `{"and": [{"glob": ["*.md", {"var": "path"}]}, {"regexp": [".*Client X.*", {"var": "content"}]}]}`)
  2. Llama a `obsidian_get_file_contents` utilizando:
     * `query_params`: `filepath` (la ruta absoluta o relativa en el vault al archivo `.md` de la minuta de reunión resuelta en el paso anterior)
  3. Resume los compromisos principales, decisiones clave, responsables y fechas detallados en la nota y se los presenta al usuario.
