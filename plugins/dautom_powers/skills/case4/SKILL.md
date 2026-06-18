---
name: case4
description: "Sub-enrutador para el Caso 4: Ask Dautom. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 4."
---

# Caso 4: Ask Dautom (Sub-Router)

Evalúa la intención del usuario y delega la ejecución de inmediato a una o más de las siguientes sub-skills de escenario específicas:

| Sub-Skill de Escenario | Escenario Asociado | Propósito / Intención del Usuario |
| :--- | :--- | :--- |
| `c4_doc_lookup` | **Concept / Documentation Lookup** | Buscar guías, manuales o explicaciones de temas generales en Obsidian. |
| `c4_meeting_minutes` | **Retrieve Meeting Minutes** | Buscar actas de reuniones, compromisos o decisiones de clientes específicos. |
| `c4_tagged_knowledge` | **Consolidate Tagged Knowledge** | Consolidar notas que compartan etiquetas temáticas (ej. #onboarding). |
| `c4_cross_reference` | **Cross-Context Reference Lookup** | Buscar especificaciones o notas técnicas vinculadas a tareas o proyectos de Zoho Sprints. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Si la solicitud del usuario coincide con uno de los escenarios descritos, carga e invoca directamente la skill de escenario correspondiente.
2. **Encadenamiento:** Permite búsquedas cruzadas complejas encadenando la recuperación de documentos con la consolidación de etiquetas si el usuario lo solicita.
3. **Resolución de Contexto:** Si se requiere mapear elementos de Zoho, delega en la skill interna `case0` para obtener la información del item/proyecto antes de consultar en Obsidian.
