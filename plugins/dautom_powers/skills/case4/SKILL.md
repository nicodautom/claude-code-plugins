---
name: case4
description: "Sub-enrutador para el Caso 4: Ask Dautom. Clasifica la intención específica del usuario y delega la ejecución a la skill de escenario correspondiente de Case 4."
---
# Caso 4: Ask Dautom (Sub-Router)
Evalúa y delega a las sub-skills correspondientes:

| Sub-Skill | Escenario | Intención |
| :--- | :--- | :--- |
| `c4_doc_lookup` | Concept / Documentation Lookup | Búsqueda y lectura de guías o notas. |
| `c4_meeting_minutes` | Retrieve Meeting Minutes | Buscar minutas y actas de reuniones. |
| `c4_tagged_knowledge` | Consolidate Tagged Knowledge | Consolidar notas con etiquetas (#tag). |
| `c4_cross_reference` | Cross-Context Reference Lookup | Buscar notas Obsidian asociadas a tareas Zoho. |

## ⚡ Reglas de Enrutamiento
1. **Delegación Inmediata:** Invoca y ejecuta la skill de escenario en esta respuesta.
2. **Encadenamiento:** Ejecuta en secuencia si abarca varias búsquedas.
3. **Resolución:** Llama a `case0` si requiere cruzar datos de Zoho Sprints.

## 🛑 Debugging y Fallos
Si la lógica falla, faltan prerrequisitos o una herramienta MCP da error:
1. **Detén la ejecución** inmediatamente.
2. **No adivines ni inventes datos** (IDs, parámetros o rutas).
3. **Reporta al usuario** el paso fallido con el error y solicita instrucciones.
