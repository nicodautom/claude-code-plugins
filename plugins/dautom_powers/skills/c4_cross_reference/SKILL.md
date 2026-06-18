---
name: c4_cross_reference
description: "Busca y asocia especificaciones técnicas o notas en Obsidian vinculadas a una tarea o proyecto de Zoho Sprints."
---

# Escenario: Cross-Context Reference Lookup

* **Intención:** "Are there any technical guides or meeting notes in Obsidian for task #1234?"
* **Dependencias:** Llama a la skill interna `case0` para obtener la información detallada (título, descripción) del item en Zoho Sprints.
* **Flujo de Acción:**
  1. Utiliza el ID técnico y palabras clave del título del item de Zoho para realizar una búsqueda mediante `obsidian_simple_search`.
  2. Si se encuentran coincidencias directas, lee las notas y presenta las guías técnicas correspondientes.
  3. Si no hay coincidencias directas, realiza una búsqueda temática sobre el proyecto para proveer documentación general.
