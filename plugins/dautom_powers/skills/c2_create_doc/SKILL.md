---
name: c2_create_doc
description: "Crea nuevas notas técnicas, minutas o guías en formato Markdown dentro del vault de Obsidian."
---

# Escenario: Create Project Documentation

* **Intención:** "Create a documentation note under 'Projects/Beta' named 'Release Notes v1.1'"
* **Dependencias:** Ninguna (interactúa localmente con el vault de Obsidian).
* **Flujo de Acción:**
  1. Procesa la ruta del archivo y valida que tenga extensión `.md`.
  2. Llama a `obsidian_put_content` enviando la ruta completa (`filepath`) y el contenido formateado en Markdown.
  3. Devuelve al usuario una confirmación con un enlace de acceso local formatted como: `[Nombre del archivo](file:///...)`.
