---
description: How performance on Explorer is calculated
sidebar_label: 'Calculations'
sidebar_position: 3
---

# Performance Calculations

:::info Macro vs Micro
In committee‑based consensus, “micro” is **per committee**, and “macro” aggregates **across all committees** the operator participates in.
:::

## Micro score (per committee)

**If no proposals occurred** in the measured window:
     $$
   Performance_{\text{micro}} = (\dfrac{σ_v}{µ_v}) \times 100
   $$
where 
- ${σ_v}$ duties successfully completed by validator ${v}$
- ${µ_v}$ duties assigned to validator ${v}$.

**Otherwise** (weighted):

  `micro = [ (5/8)·( Σ_s∈S_std σ_s / Σ_s∈S_std µ_s ) + (3/8)·( Σ_s∈S_prop σ_s / Σ_s∈S_prop µ_s ) ] × 100`

     $$
   Performance_{\text{micro}} = (\dfrac{σ_v}{µ_v}) \times 100
   $$

## Macro score (operator aggregate across committees)

Let **G** be the set of committees the operator served.

* **If no proposals occurred in any committee**:

  `macro = ( Σ_g∈G Σ_s∈S_g σ_s / Σ_g∈G Σ_s∈S_g µ_s ) × 100`

* **Otherwise** (weighted per Duty Score across committees):

  `macro = [ (5/8)·( Σ_g∈G Σ_s∈S_std,g σ_s / Σ_g∈G Σ_s∈S_std,g µ_s ) + (3/8)·( Σ_g∈G Σ_s∈S_prop,g σ_s / Σ_g∈G Σ_s∈S_prop,g µ_s ) ] × 100`