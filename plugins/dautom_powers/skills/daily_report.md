---
name: daily-report
description: >
  Úsalo para recopilar las notas modificadas recientemente en Obsidian, elaborar un resumen estructurado del día e inyectarlo en la Nota Diaria correspondiente.
---

# Daily Report Generator Execution

Esta skill detalla los pasos exactos de procesamiento y las reglas que Claude debe seguir al ejecutar el comando para generar y registrar el reporte diario en Obsidian.

## Paso 1 — Definición de Rango Temporal
- Identificar el periodo del reporte (por defecto, las últimas 24 horas).
- Calcular la fecha actual del sistema para buscar la nota del periodo correspondiente.

## Paso 2 — Extracción de Modificaciones
- Ejecutar `obsidian_get_recent_changes`.
- Filtrar los resultados para excluir notas de sistema o de registro automático si no aportan valor.
- De ser necesario, leer el contenido de las notas principales modificadas usando `obsidian_batch_get_file_contents` para sintetizar el trabajo realizado en cada una.

## Paso 3 — Estructuración del Reporte
- Crear una sección limpia con la siguiente estructura:
  ```markdown
  ## Resumen del Día ([Fecha])
  - **Archivos editados:**
    - [[Nota Editada 1]]: Descripción breve del cambio o tema.
    - [[Nota Editada 2]]: Descripción breve del cambio o tema.
  - **Resumen de Actividades:**
    - [Logros y temas abordados durante el día]
  ```

## Paso 4 — Inyección en la Nota Diaria
- Buscar la nota diaria usando `obsidian_get_periodic_note` (period="daily").
- Leer la nota actual para determinar el mejor punto de inserción (normalmente al final de la nota).
- Utilizar `obsidian_append_content` para insertar el reporte estructurado de forma no destructiva.
- Confirmar al usuario mostrando un resumen corto en texto de lo que se guardó.

## Casos de Uso Comunes
- *"Genera el reporte de mi trabajo de hoy y guárdalo en mi nota diaria."*
- *"Revisa qué archivos modifiqué en Obsidian esta semana y hazme un resumen para mi reunión de seguimiento."*
