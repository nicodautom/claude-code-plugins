---
name: activity-log-reviewer
description: >
  Úsalo para consultar, consolidar y reportar registros de tiempo (time logs) y la actividad realizada por el usuario en Zoho Sprints en un periodo de tiempo determinado.
---

# Activity & Log Reviewer Execution

Esta skill define la lógica para recuperar, calcular y presentar de forma comprensible el resumen de registros de tiempo y actividad de un usuario en Zoho Sprints.

## Paso 1 — Determinación del Periodo de Consulta
- Analizar el rango de tiempo solicitado por el usuario (ej. "esta semana", "hoy", "del 1 al 5 de junio").
- Convertir estas expresiones temporales a fechas específicas con formato `yyyy-MM-dd` para los parámetros `fromDate` y `toDate`.

## Paso 2 — Recuperación de los Datos
- Llamar a `ZohoSprints_GetLogHours` con los parámetros de fecha configurados y el ID de usuario.
- De ser necesario, iterar sobre los logs obtenidos para obtener detalles de las tareas si la respuesta original contiene solo IDs parciales.

## Paso 3 — Cálculo y Agrupamiento
- Sumar todas las horas registradas. Convertir los formatos `HH:MM` a un total decimal o a un formato acumulado (ej. "15 horas y 30 minutos").
- Agrupar los registros por tarea y enlistar las descripciones/notas asociadas a cada log de tiempo.

## Paso 4 — Presentación en Markdown
- Formatear el reporte con un diseño premium y ordenado:
  - **Periodo Evaluado:** [Rango de fechas]
  - **Total de Horas Registradas:** [Suma total]
  - **Detalle de Actividades:**
    | Tarea | Duración | Descripción/Nota del Log | Fecha |
    | --- | --- | --- | --- |
    | [Tarea A] | 02:00 | "Se implementó la sección..." | 2026-06-11 |
    | [General] | 01:00 | "Reunión técnica" | 2026-06-11 |

## Casos de Uso Comunes
- *"Muéstrame todo el tiempo que he registrado esta semana y en qué tareas ha sido."*
- *"Genera un reporte de todo lo que he trabajado hoy (logs y descripciones) para enviarlo a mi equipo."*
- *"¿Cuántas horas llevo registradas en el proyecto actual y cuáles han sido las notas de esos logs?"*
