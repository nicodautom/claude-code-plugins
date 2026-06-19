---
name: case0
description: "Módulo de resolución de dependencias y mapeo de IDs técnicos de Zoho Sprints (proyectos, sprints, tareas, épicas y checklists)."
---
# Caso 0: Resolving Context and Dependencies
Mapea nombres y referencias generales a identificadores técnicos de Zoho Sprints.

## 📌 Contexto Inicial
* **Workspace ID (`teamId`):** ID obtenido del contexto o sesión de Zoho Sprints.
* **User ID (`userId`):** ID del usuario actual de Zoho Sprints.
* **Cabeceras Obligatorias:** Para toda llamada de Zoho Sprints, incluye siempre: `headers={"x-za-ui-version": "v2", "X-convert-response": "true"}`.

## 📋 Resolución de Identificadores

### 1. Proyecto (`projectId`)
* Llama a `ZohoSprints_GetProjects` con: `path_variables={"teamId"}` y `query_params={"action": "data", "index": 1, "range": 100}`.
* Busca por nombre en la propiedad `name`.

### 2. Sprint Activo (`sprintId`)
* Llama a `ZohoSprints_GetSprints` con: `path_variables={"teamId", "projectId"}` y `query_params={"action": "data", "index": 1, "range": 50, "type": "[2]"}`.

### 3. Backlog (`sprintId` para Backlog)
* Llama a `ZohoSprints_GetProjectDetails` con: `path_variables={"teamId", "projectId"}` y `query_params={"action": "getbacklog"}`.
* Extrae la propiedad `backlogId`.

### 4. Tarea (`itemId`)
* Llama a `ZohoSprints_GetItems` con: `path_variables={"teamId", "projectId", "sprintId"}` y `query_params={"action": "data", "index": 1, "range": 250}`.
* Si es referencia (ej. "#ID"), busca en `itemNo`. Si es texto, busca en `itemName`.

### 5. Épica (`epicId`)
* Llama a `ZohoSprints_GetEpics` con: `path_variables={"teamId", "projectId"}` y `query_params={"action": "data", "index": 1, "range": 100}`.
* Busca por nombre en la propiedad `name`.

### 6. Grupo de Checklist (`clGroupId`) y Sub-item (`clItemId`)
* Llama a `ZohoSprints_GetChecklistGroups` con: `path_variables={"teamId", "projectId", "sprintId", "itemId"}` y `query_params={"action": "data", "index": 1, "range": 100}` para `clGroupId`.
* Llama a `ZohoSprints_GetChecklists` con: `path_variables={"teamId", "projectId", "sprintId", "itemId", "clGroupId"}` y `query_params={"action": "data", "index": 1, "range": 100}` para `clItemId`.

### 7. Módulo (`moduleId`) para Comentarios
* Usa el ID predeterminado de tareas: `"61978000000002009"`.
* Alternativamente, lee las llaves de `moduleIdvsLayoutId` en `ZohoSprints_GetProjectDetails` con `action="details"`.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
