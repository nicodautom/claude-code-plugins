# Command: Activity & Log Reviewer

## Descripción
Este comando permite al usuario consultar todos los registros de tiempo (time logs) y la actividad realizada en Zoho Sprints durante un período específico (como el día de hoy, la última semana o un rango de fechas personalizado), consolidando las horas totales trabajadas y las descripciones.

## How To (Uso de Herramientas)
Para ejecutar este comando, el asistente debe seguir estas pautas usando las herramientas de Zoho Sprints:

1. **Obtener logs de horas**: Usar `ZohoSprints_GetLogHours` configurando los parámetros de filtrado por usuario y rango de fechas (ej. `fromDate` y `toDate`) para obtener todos los registros de tiempo de ítems y registros generales.
2. **Revisar actividad adicional (opcional)**: Usar `ZohoSprints_GetItemActivity` en las tareas del usuario para complementar el informe con cambios de estado y comentarios hechos en el período.
3. **Consolidar y estructurar**: Sumar la duración total de las horas trabajadas en el rango seleccionado, clasificar los logs por tarea y generar un reporte ejecutivo del período.
