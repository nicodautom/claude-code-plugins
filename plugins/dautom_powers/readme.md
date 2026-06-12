# Plugin: dautom_powers

Este es un plugin para Claude (tanto Desktop como Code) diseñado para facilitar la administración y gerencia de proyectos, actividades, registros de tiempo, y tareas en Zoho Sprints, así como la consulta y actualización estructurada de notas y conocimientos en Obsidian.

## Estructura del Plugin

El plugin está estructurado de la siguiente forma:

- **`.claude-plugin/`**: Contiene la configuración y metadatos del plugin.
  - `plugin.json`: Metadatos generales (nombre, versión, descripción, autor).
- **`commands/`**: Define los comandos que Claude puede recibir, junto con una explicación de qué herramientas de los servidores MCP de Zoho y Obsidian debe usar ("How To").
  - `knowledge_retrieval.md`: Búsqueda avanzada y consulta en Obsidian.
  - `daily_report.md`: Generación automática de reportes de final de día.
  - `time_activity_logger.md`: Registro rápido de horas (asociado a tareas o general).
  - `sprint_project_overview.md`: Resumen general del sprint y tareas asignadas.
  - `task_status_manager.md`: Cambio de estados y comentarios en Zoho Sprints.
  - `activity_log_reviewer.md`: Revisión y sumatoria de horas y actividades del día/semana.
- **`skills/`**: Contiene las instrucciones paso a paso detalladas que le explican a Claude exactamente cómo procesar la información y ejecutar cada comando.
  - `knowledge_retrieval/SKILL.md`
  - `daily_report/SKILL.md`
  - `time_activity_logger/SKILL.md`
  - `sprint_project_overview/SKILL.md`
  - `task_status_manager/SKILL.md`
  - `activity_log_reviewer/SKILL.md`
- **`agents/`**: Define el perfil, comportamiento, tono y directrices del agente que interactuará con el usuario.
  - `dautom_manager.md`: Perfil del agente "Dautom Manager".

## Servidores MCP Utilizados

- **ZohoSprints**: Para la creación, edición, movimiento y logging de tareas.
- **Obsidian**: Para la búsqueda, lectura y actualización de notas diarias y base de conocimientos.
