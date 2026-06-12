# Skill: Sprint & Project Overview Execution

Esta skill detalla los pasos exactos de procesamiento y formato que Claude debe seguir al estructurar un reporte sobre el estado de un proyecto o sprint.

## Instrucciones Paso a Paso

1. **Identificación del Contexto del Proyecto**:
   - Detectar si el usuario se refiere a un proyecto en específico. Si no, usar el proyecto por defecto o solicitar aclaración.
   - Llamar a `ZohoSprints_GetSprints` o `ZohoSprints_GetSprintDetails` para obtener la información del sprint en curso.

2. **Obtención y Filtro de Tareas**:
   - Llamar a `ZohoSprints_GetItems` pasando el `sprintId` obtenido.
   - Si el usuario solicita ver sus propias tareas, filtrar los ítems de acuerdo con el ID de usuario del asignado (`assignee`).

3. **Estructuración y Presentación del Reporte**:
   - Formatear la información en markdown utilizando tablas y listas.
   - El reporte debe incluir:
     - **Detalles del Sprint**: Nombre del sprint, fechas de duración y estado.
     - **Resumen Numérico**: Cantidad total de tareas, tareas cerradas vs pendientes.
     - **Secciones de Tareas**:
       - `### Por Hacer (To Do)`
       - `### En Progreso (In Progress)`
       - `### Completado (Closed)`
     - Cada tarea debe mostrar su ID, título y el responsable de manera resumida.

## Casos de Uso Comunes
- *"Dame un resumen de cómo vamos en el sprint actual y qué tareas me faltan por terminar."*
- *"¿Cuáles son las tareas de alta prioridad (High) que no hemos empezado en este proyecto?"*
- *"Muestra el progreso del sprint actual."*
