---
name: c2_create_doc
description: "Crea o actualiza documentos y especificaciones en Obsidian bajo carpetas estructuradas."
---
# Create Project Documentation
* **Intención:** Crear o estructurar documentos técnicos en Obsidian.
* **Acciones:**
  1. Obtén del usuario el nombre y el contenido estructurado del documento.
  2. Valida la carpeta de destino en el vault (creando carpetas si es necesario).
  3. Llama a `obsidian_put_content` con:
     * `query_params`: `filepath` (ruta y nombre `.md`), `content` (documento en Markdown)
  4. Muestra confirmación con enlace directo.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
