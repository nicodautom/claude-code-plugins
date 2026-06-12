# Command: Daily Report Generator

## Descripción
Este comando automatiza la compilación del trabajo diario recopilando todos los archivos modificados o creados recientemente en el vault de Obsidian, elaborando un resumen ejecutivo e inyectándolo de forma ordenada dentro de la nota diaria (Daily Note).

## How To (Uso de Herramientas)
Para ejecutar este comando, el asistente debe seguir estas pautas usando las herramientas del servidor MCP de Obsidian:

1. **Obtener cambios recientes**: Usar `obsidian_get_recent_changes` configurando un marco temporal de las últimas 24 horas (u otro periodo indicado) para listar los archivos modificados.
2. **Localizar la nota diaria**: Usar `obsidian_get_periodic_note` con el parámetro `period="daily"` (o "weekly" si se solicita un reporte semanal) para abrir o crear la nota diaria correspondiente a la fecha de hoy.
3. **Leer las notas modificadas (opcional)**: Usar `obsidian_get_file_contents` para revisar los cambios específicos si el resumen de la herramienta de cambios recientes no tiene suficiente detalle.
4. **Escribir el reporte**: Estructurar un bloque de texto que resuma los logros del día bajo el título `## Resumen del Día`. Escribir o anexar este bloque a la nota diaria utilizando `obsidian_append_content` o `obsidian_patch_content`.
