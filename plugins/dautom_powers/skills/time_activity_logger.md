---
name: time-activity-logger
description: >
  Úsalo cuando el usuario necesite registrar horas trabajadas (de forma general o asociadas a una tarea específica) en Zoho Sprints.
---

# Time & Activity Logger Execution

Esta skill detalla las pautas que Claude debe seguir para asegurar que los registros de tiempo en Zoho Sprints sean precisos y contengan la descripción correcta.

## Paso 1 — Recolección de Información
- Extraer la duración (ej. "2 horas", "30 mins", "1.5h").
- Extraer el nombre o descripción de la tarea y la nota del log.
- Determinar si es un log asociado a un item específico (Task) o general (General).

## Paso 2 — Resolución de Identificadores (IDs)
- Identificar el proyecto activo. Si no está definido en el contexto, buscarlo usando `ZohoSprints_GetProjects`.
- Si se trata de una tarea, buscar su `itemId` invocando `ZohoSprints_GetItems` con `searchvalue` igual al título o palabras claves de la tarea.
- Si hay múltiples tareas coincidentes, listar las opciones al usuario y pedir confirmación antes de registrar.

## Paso 3 — Formateo de la Duración
- Convertir la duración proporcionada al formato `HH:MM` requerido por la API (ej. "1.5 horas" -> "01:30", "45 minutos" -> "00:45").

## Paso 4 — Registro y Confirmación
- Ejecutar `ZohoSprints_AddItemLogHours` o `ZohoSprints_AddGeneralLogHours`.
- Proporcionar una descripción clara del trabajo realizado.
- Confirmar al usuario con un resumen estructurado indicando:
  - **Proyecto:** [Nombre del proyecto]
  - **Tarea:** [Nombre de la tarea u "Horas Generales"]
  - **Duración:** [Horas registradas]
  - **Descripción:** [Descripción del log]

## Casos de Uso Comunes
- *"Registra 3 horas a la tarea de 'Creación de Skills' y pon de nota que terminé la parte de Obsidian."*
- *"Añade 1 hora de log general por la reunión de seguimiento (Daily)."*
- *"Registra 1 hora y media en el diseño de interfaces."*
