# Command: Task & Status Manager

## Descripción
Este comando permite al usuario actualizar el estado de sus tareas (por ejemplo: marcarlas como completadas, en progreso o bloqueadas), reasignarlas o agregar comentarios sobre bloqueos y avances importantes directamente desde la interfaz conversacional.

## How To (Uso de Herramientas)
Para ejecutar este comando, el asistente debe seguir estas pautas usando las herramientas de Zoho Sprints:

1. **Localizar la tarea**: Usar `ZohoSprints_GetItems` con `searchvalue` para encontrar el `itemId` correcto basándose en la solicitud del usuario.
2. **Actualizar estado / campos**: Llamar a `ZohoSprints_UpdateItem` pasando el `projectId`, `itemId` y los campos que se desean modificar (como `statusid` para cambiar el estado).
3. **Agregar comentarios de seguimiento**: Si el usuario menciona un motivo de bloqueo o una nota sobre el cambio, usar `ZohoSprints_AddItemComment` con el `itemId` y el texto del comentario en `commentContent`.
