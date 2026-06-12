# Command: Sprint & Project Overview

## Descripción
Este comando genera una visualización estructurada e informativa sobre el progreso general del sprint activo, detallando las tareas pendientes, los responsables y el estado del proyecto para ayudar en la planeación diaria o la preparación de reuniones.

## How To (Uso de Herramientas)
Para ejecutar este comando, el asistente debe seguir estas pautas usando las herramientas de Zoho Sprints:

1. **Obtener proyectos**: Si no se conoce el ID del proyecto, usar `ZohoSprints_GetProjects` para listar los proyectos activos.
2. **Obtener sprints**: Usar `ZohoSprints_GetSprints` o `ZohoSprints_GetSprintDetails` para identificar el sprint activo y conocer sus fechas de inicio y fin, así como su estado general.
3. **Listar tareas**: Usar `ZohoSprints_GetItems` con el `sprintId` correspondiente para recuperar la lista completa de tareas de dicho sprint.
4. **Resumir información**: Agrupar los ítems recuperados por estado (ej. "To Do", "In Progress", "Closed") y opcionalmente por asignado.
