# Skill: Task & Status Manager Execution

Esta skill detalla las pautas y el orden de ejecución para realizar modificaciones de estado y de comentarios en los Work Items de Zoho Sprints.

## Instrucciones Paso a Paso

1. **Búsqueda e Identificación**:
   - Identificar el nombre de la tarea mencionada.
   - Realizar la búsqueda usando `ZohoSprints_GetItems`.
   - Si se encuentran múltiples tareas similares, solicitar al usuario que elija la correcta indicando su ID y título.

2. **Actualización de Estado**:
   - Mapear la intención del usuario al ID de estado correspondiente del proyecto. Por ejemplo:
     - "completar", "terminar", "cerrar" -> Estado `Closed` (o ID correspondiente).
     - "empezar", "en progreso", "desarrollando" -> Estado `In Progress` (o ID correspondiente).
     - "bloqueado", "pausado", "en espera" -> Estado `Blocked` (o ID correspondiente).
   - Ejecutar `ZohoSprints_UpdateItem` con el `itemId` y el nuevo `statusid`.

3. **Inclusión de Comentarios y Notas**:
   - Si el usuario proporciona una justificación o detalle para el cambio (ej. "Pon la tarea en bloqueada porque falta el diseño"), llamar a `ZohoSprints_AddItemComment` de manera consecutiva para documentar la causa.

4. **Confirmación**:
   - Confirmar al usuario de manera clara que la tarea ha sido actualizada, listando su nuevo estado y los comentarios agregados.

## Casos de Uso Comunes
- *"Ya terminé la tarea de 'Revisión de Base de Datos', pásala a completada."*
- *"Pon la tarea X en estado 'Blocked' y añádele un comentario diciendo que estamos esperando respuesta del cliente."*
- *"Reasigna la tarea de diseño del login a Juan."*
