---
name: c4_cross_reference
description: "Busca y asocia especificaciones técnicas o notas en Obsidian vinculadas a una tarea o proyecto de Zoho Sprints."
---
# Cross-Context Reference Lookup
* **Intención:** Buscar notas o especificaciones asociadas a una tarea de Zoho Sprints.
* **Dependencias:** `case0` para obtener título y descripción del item en Zoho Sprints.
* **Acciones:**
  1. Llama a `obsidian_simple_search` con:
     * `query_params`: `query` (ID numérico de la tarea o palabras clave del título del item)
  2. Lee y presenta las notas y especificaciones técnicas correspondientes.
  3. Si no hay coincidencia directa, realiza una búsqueda general del proyecto en Obsidian.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
