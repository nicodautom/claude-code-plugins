---
name: knowledge-retrieval
description: "Úsalo cuando necesites buscar, consultar o resumir información específica dentro de la base de conocimientos de Obsidian para responder preguntas."
---

# Knowledge Retrieval & Q&A Execution

Esta skill detalla los pasos exactos de procesamiento y las reglas que Claude debe seguir al ejecutar el comando de búsqueda de conocimiento en Obsidian.

## Paso 1 — Análisis de la Intención del Usuario
- Identificar los conceptos y palabras clave principales de la pregunta del usuario.
- Determinar si la búsqueda debe limitarse a una carpeta específica, un tag o si es general.

## Paso 2 — Estrategia de Búsqueda
- Ejecutar la búsqueda inicial utilizando `obsidian_simple_search`.
- Si se requiere una búsqueda estructurada por etiquetas, utilizar `obsidian_search_by_tag`.
- Si no hay resultados directos, intentar sinónimos o variantes lingüísticas de las palabras clave.

## Paso 3 — Lectura y Selección de Documentos
- Inspeccionar los fragmentos devueltos en la búsqueda.
- Leer el contenido de las notas más relevantes usando `obsidian_batch_get_file_contents` o `obsidian_get_file_contents`.
- *Regla*: Evitar leer más de 10 notas simultáneamente para optimizar el contexto.

## Paso 4 — Síntesis y Formulación de Respuestas
- Redactar una respuesta estructurada, clara y directa.
- Utilizar secciones y listas cuando sea apropiado.
- **Formato de Enlaces**: Siempre incluir enlaces markdown a las notas de origen usando la sintaxis `[[Nombre de la Nota]]` o links con formato `[Texto](file:///...)` si se requiere la ruta absoluta del archivo para abrirlo directamente en el editor.

## Casos de Uso Comunes
- *"¿Cuáles fueron las conclusiones de la última reunión de diseño?"*
- *"Búscame la documentación del proyecto X y hazme un resumen."*
- *"Revisa mis notas con tag #ideas y relaciónalas con marketing."*
