---
name: c4_meeting_minutes
description: "Busca y resume actas de reuniones o compromisos de un cliente en el vault de Obsidian."
---

# Escenario: Retrieve Meeting Minutes

* **Intención:** "Find the minutes of the kick-off meeting with Client X"
* **Flujo de Acción:**
  1. Llama a `obsidian_complex_search` utilizando filtros por nombre del cliente y carpetas de actas/minutas de reuniones.
  2. Llama a `obsidian_get_file_contents` para leer el archivo de la reunión correspondiente.
  3. Resume los compromisos principales, decisiones clave, responsables y fechas detallados en la nota y se los presenta al usuario.
