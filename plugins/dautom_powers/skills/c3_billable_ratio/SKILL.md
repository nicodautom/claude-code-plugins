---
name: c3_billable_ratio
description: "Calcula el ratio de horas facturables contra el total de horas registradas, evaluando si cumple con el target del 70%."
---

# Escenario: Billable Hours Ratio (70% Target)

* **Intención:** "Check if my logged hours this month met the 70% billable target"
* **Dependencias:** Llama a la skill interna `case0` para obtener el `projectId` y el `userId` (si se consulta un compañero).
* **Flujo de Acción:**
  1. Llama a `ZohoSprints_GetLogHours` utilizando `teamId` y `projectId`, con `listviewtype=1` (por usuario) y rango de fechas.
  2. Filtra los logs por el ID del usuario.
  3. Calcula:
     * Horas Totales ($H_{total}$).
     * Horas Facturables ($H_{billable}$, donde `isbillable=1`).
     * Ratio: $R = \frac{H_{billable}}{H_{total}} \times 100$.
  4. Compara el ratio $R$ contra la meta del 70% y presenta el resultado (Met target: Yes/No, Ratio, horas facturables y no facturables).
