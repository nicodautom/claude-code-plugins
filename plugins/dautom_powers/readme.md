# Plugin: dautom_powers

Este es un plugin para Claude (tanto Desktop como Code) diseñado para facilitar la administración y gerencia de proyectos, actividades, registros de tiempo, y tareas en Zoho Sprints, así como la consulta y actualización estructurada de notas y conocimientos en Obsidian.

## Estructura del Plugin

El plugin está estructurado de la siguiente forma:

- **`.claude-plugin/`**: Contiene la configuración y metadatos del plugin.
  - `plugin.json`: Metadatos generales (nombre, versión, descripción, autor).
- **`agents/`**: Define el perfil, comportamiento, tono y directrices del agente que interactuará con el usuario.
  - `dautom_manager.md`: Perfil del agente "Dautom Manager".
- **`skills/`**: Contiene la estructura de skills en árbol (enrutadores y módulos de ejecución):
  - **`dautom_router/`**: Enrutador central que clasifica la intención del usuario ante consultas generales o ambiguas.
  - **`case0/`**: Módulo de resolución de dependencias, mapeando nombres comunes a IDs técnicos de Zoho Sprints de forma silenciosa.
  - **Sub-enrutadores de Casos:**
    - `case1/`: Sub-ruteador para el Caso 1 (Daily or status report).
    - `case2/`: Sub-ruteador para el Caso 2 (Documentation and logs).
    - `case3/`: Sub-ruteador para el Caso 3 (KPIs report).
    - `case4/`: Sub-ruteador para el Caso 4 (Ask Dautom / Obsidian).
  - **Skills de Escenario (Hojas de Ejecución):**
    - `c1_*`: 5 skills específicas de escenarios para reportes diarios y de sprints.
    - `c2_*`: 9 skills específicas de escenarios para registros, checklists y notas.
    - `c3_*`: 6 skills específicas de escenarios para KPIs y dashboards.
    - `c4_*`: 4 skills específicas de escenarios para búsquedas y consultas cruzadas en Obsidian.

## Servidores MCP Utilizados

- **ZohoSprints**: Para la creación, edición, movimiento y logging de tareas.
- **Obsidian**: Para la búsqueda, lectura y actualización de notas diarias y base de conocimientos.
