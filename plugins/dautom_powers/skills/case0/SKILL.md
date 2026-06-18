---
name: case0
description: "Módulo de resolución de dependencias y mapeo de IDs técnicos de Zoho Sprints (proyectos, sprints, tareas, épicas y checklists)."
---

# Caso 0: Resolving Context and Dependencies

Esta skill interna define las instrucciones y los flujos de herramientas MCP requeridos para mapear nombres comunes a IDs técnicos de Zoho Sprints.

## 📌 Contexto Global
El agente debe recuperar de su memoria persistente o contexto de sesión los identificadores iniciales:
* **Workspace ID (`teamId`):** ID del espacio de trabajo de Zoho Sprints.
* **User ID (`userId`):** ID técnico del usuario de Zoho.

---

## 📋 Escenarios de Resolución de IDs

### 1. Resolve Project ID (`projectId`) by Name
* **Entrada:** Nombre del Proyecto.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetProjects` con el `teamId` y parámetros `action="data"`, `index=1`, `range=100`, y `searchvalue=[Nombre del Proyecto]`.
  2. Filtra la lista para encontrar la coincidencia exacta o más cercana en la propiedad `name`.
  3. Extrae y almacena el `projectId` en memoria.

### 2. Resolve Active Sprint ID (`sprintId`)
* **Entrada:** `projectId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetSprints` con `teamId`, `projectId`, y parámetros `action="data"`, `index=1`, `range=50`, y `type="2"` (donde tipo 2 indica Sprint Activo).
  2. Extrae el `sprintId` del sprint activo devuelto.

### 3. Resolve Backlog Sprint ID (`sprintId`)
* **Entrada:** `projectId`.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetProjectDetails` con `teamId`, `projectId`, y parámetro `action="getbacklog"`.
  2. Extrae el ID único asignado al backlog del proyecto para usarlo como `sprintId`.

### 4. Resolve Item ID (`itemId`) by Name or Reference
* **Entrada:** `projectId` (opcional), `sprintId` (opcional), Referencia de Tarea (ej. "#123") o Nombre de la Tarea.
* **Flujo de Acción:**
  1. Si `projectId` y `sprintId` no se especifican en la consulta del usuario, asume por defecto el proyecto activo configurado en la memoria de contexto de sesión del agente.
  2. Si no hay un proyecto activo en memoria o no se encuentra la tarea en él, llama a `ZohoSprints_GetProjects` para obtener la lista de proyectos activos de la cuenta actual e itera en sus sprints activos buscando el item.
  3. Llama a `ZohoSprints_GetItems` con el `teamId` de sesión, el `projectId` resuelto, el `sprintId` resuelto, y el parámetro `searchvalue=[Referencia o Nombre]`.
  4. Si es una referencia numérica (ej. #123), busca la coincidencia exacta con la propiedad `key`. Si es texto, realiza una búsqueda en los nombres de tarea devueltos.
  5. Recupera y almacena el `itemId`.

## ⏱️ Reglas de Contexto de Tiempo y Fechas
* Para calcular fechas relativas (ej. "ayer", "el lunes pasado", "hace dos días"), debes usar siempre como base la fecha y hora del sistema provista en tus metadatos iniciales de sesión.
* Convierte las fechas calculadas al formato estricto `YYYY-MM-DD` antes de utilizarlas en cualquier llamada MCP de Zoho Sprints.
* Convierte las duraciones de tiempo a formato de hora estricto `HH:MM` (ej. 3.5h -> "03:30", 45m -> "00:45").

### 5. Resolve Epic ID (`epicId`) by Name
* **Entrada:** `projectId`, Nombre de la Épica.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetEpics` con `teamId`, `projectId`, y parámetro `searchvalue=[Nombre de la Épica]`.
  2. Mapea la épica y extrae su `epicId` correspondiente.

### 6. Resolve Checklist Group ID (`clGroupId`) and Item ID (`clItemId`)
* **Entrada:** `projectId`, `sprintId`, `itemId`, Nombre de Grupo de Checklist y Nombre del Item.
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetChecklistGroups` con `teamId`, `projectId`, `sprintId`, e `itemId`. Busca el `clGroupId` correspondiente al nombre del grupo.
  2. Llama a `ZohoSprints_GetChecklists` con `teamId`, `projectId`, `sprintId`, `itemId` y `clGroupId` para mapear el `clItemId` individual.
