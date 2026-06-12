---
name: knowledge-retrieval
description: "Busca y resume información dentro de la base de conocimientos de Obsidian."
---

# Command: Knowledge Retrieval & Q&A

## Descripción
Este comando permite a Claude buscar de manera proactiva e inteligente en la base de conocimientos de Obsidian para responder preguntas, resumir temas específicos o recopilar contexto relevante de las notas del usuario.

## How To (Uso de Herramientas)
Para ejecutar este comando, el asistente debe seguir estas pautas usando las herramientas del servidor MCP de Obsidian:

1. **Buscar notas relevantes**: Usar `obsidian_simple_search` o `obsidian_complex_search` con palabras clave extraídas del prompt del usuario para localizar notas relacionadas.
2. **Consultar metadatos**: Si es necesario filtrar por tags o propiedades específicas de frontmatter, usar `obsidian_get_frontmatter` u `obsidian_search_by_tag`.
3. **Leer contenido**: Utilizar `obsidian_get_file_contents` o `obsidian_batch_get_file_contents` para extraer el contenido completo de las notas identificadas.
4. **Analizar y sintetizar**: Procesar la información de las notas leídas, responder a la consulta del usuario y citar explícitamente las fuentes usando enlaces markdown a las notas de Obsidian.
