---
name: c4_meeting_minutes
description: "Busca y resume actas de reuniones o compromisos de un cliente en el vault de Obsidian."
---
# Retrieve Meeting Minutes
* **Intención:** Buscar y resumir minutas/actas de reuniones de clientes.
* **Acciones:**
  1. Llama a `obsidian_complex_search` con:
     * `query_params`: `query` (objeto JsonLogic para filtrar por tipo de archivo, contenido y ruta del cliente)
  2. Llama a `obsidian_get_file_contents` con:
     * `query_params`: `filepath` (ruta de la minuta seleccionada)
  3. Extrae y presenta compromisos, decisiones, responsables y fechas.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
