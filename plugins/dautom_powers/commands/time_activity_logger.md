---
name: time-activity-logger
description: "Registra horas trabajadas en una tarea específica o de forma general en Zoho Sprints."
---

# Command: Time & Activity Logger

## Descripción
Este comando facilita el registro de horas trabajadas en Zoho Sprints, asociando el tiempo a una tarea específica del sprint actual o registrando horas generales (como reuniones de equipo) a través del chat de Claude.

## How To (Uso de Herramientas)
Para ejecutar este comando, el asistente debe seguir estas pautas usando las herramientas de Zoho Sprints:

1. **Buscar la tarea**: Utilizar `ZohoSprints_GetItems` con el parámetro `searchvalue` (que coincide con el nombre o ID de la tarea dada por el usuario) para localizar el `itemId` y verificar en qué sprint se encuentra.
2. **Identificar ID de Proyecto**: Utilizar la tabla de mapeo de proyectos o llamar a `ZohoSprints_GetProjects` para obtener el `projectId` si no se especificó previamente.
3. **Registrar horas en la tarea**: Llamar a `ZohoSprints_AddItemLogHours` proporcionando `projectId`, `itemId`, la duración del registro (`duration` en formato HH:MM) y una descripción en `description`.
4. **Registrar horas generales**: Si no hay tarea directa (ej. reuniones de seguimiento, soporte general), usar `ZohoSprints_AddGeneralLogHours` con `projectId`, `duration` y `description`.
