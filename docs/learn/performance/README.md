---
description: Understanding performance metrics in the SSV network
sidebar_position: 5
---

# Performance

The operator performance metric serves as a technical scoring system for operators in the ssv network. It measures what an operator actually did across the full consensus flow — even when quorum wasn’t reached.

SSV’s consensus moved from **validator‑based** to **committee‑based** (or *cluster-based*). Each operator is credited for actions they perform (leader, prepare, commit, etc.), rather than just whether a final duty was submitted.

## How a slot is evaluated

Each **slot** a validator is assigned a **duty** (attestation, proposal, etc.). Each **duty** includes **multiple actions** to reach consensus. It can take **multiple rounds** of actions to reach consensus for one duty. Each round follows this sequence of actions:

**`leader → prepares → commits → pre‑consensus → post‑consensus`**

### Action points (per operator, per round)

Each operator in a cluster is credited for the actions completed (leader, prepare, commit, pre/post‑consensus) even if the round doesn’t finalize. That’s a core improvement over v1.

| Action                              | How it scores                                                  |
| --------------------------------- | -------------------------------------------------------------- |
| **leader**                        | **+4** if completed (single‑operator, high‑value role); else 0 |
| **prepares**                      | **+1** if completed; else 0                                    |
| **commits**                       | **+1** if completed; else 0                                    |
| **pre‑consensus** (if applicable) | **+1** if completed; else 0                                    |
| **post‑consensus**                | **+1** if achieved; else 0                                     |

### Duty type weighting

Because the block proposals are rarer and disproportionately affect rewards, they're classified separately and carry more weight than their frequency. This mirrors [Rated’s approach to RAVER score](https://docs.rated.network/documentation/methodologies/ethereum/rated-effectiveness-rating/raver-v3.0-current#effectiveness-rating).

Performance groups duties into two economic duty scores based on the duty type:

* **Standard Duty Score** contributes **5/8** of the total weight (Attestation, Sync Committee, Aggregator).
* **Proposal Duty Score** contributes **3/8** of the total weight (Block Proposal).

If the selected time range has **no proposals**, Standard accounts for **100%** of the weighted performance.

## Examples of calculation

For each slot, **σ** is the sum of points an operator **did earn** across all rounds; **µ** is the **maximum possible** an operator could have earned from duties in assigned rounds. The Explorer sums these and then applies the Standard vs Proposal weighting.

The **per‑slot maximum (µ)** is the sum of all the points the operator *can possibly* obtain from the duties in all rounds in time window.

The **per‑slot score (σ)** sums all points the operator *actually* earned across all rounds in that slot/time window. 

### Example A — No proposals (Standard only)

* Across the window, the operator could have earned **µ = 280** points and actually earned **σ = 252**.
* **Micro (or Macro) = 252 / 280 × 100 = 90%**.

In this example, no proposal duties were in a time window, so no weighting is applied.

### Example B — Standard + Proposal

* **Standard Duty Score**: µ_s = 240, σ_s = 228 → 228/240 = **95%**
* **Proposal Duty Score**: µ_p = 16, σ_p = 8 → 8/16 = **50%**
* **Weighted**: (5/8·0.95) + (3/8·0.50) = 0.78125 → **78.125%**

Here the operator completed **95%** of non-proposal duties, while only **50%** of proposal duties, resulting in **78.125%** score overall. 

Due to weighting based on duty type, missing proposal duties pulls down the overall score more than a pure average would, reflecting their higher economic weight. 

## Network Explorer

How to read the performance:
> **Find a time range** (last 1d/7d), Explorer evaluates all slots in that window where the operator had duties.
> **Micro** shows this result per committee/cluster; **Macro** combines all committees.

Operator's scores and performance can be viewed in corresponding operator pages and also per each cluster at:

* [SSV Network Explorer](https://explorer.ssv.network)
* [SSV Scan](https://ssvscan.io/)
* [Monitor SSV](https://monitorssv.xyz/)

## Explorer at a glance (???)

#### Operator’s Explorer page:

* An overall performance percentage for the selected time range.
* A breakdown between **Standard Consensus** and **Proposal Consensus**, reflecting their different weights.
* **Per‑committee (“micro”)** performance and an **operator‑wide (“macro”)** aggregate across all committees the operator participates in.

#### Cluster's *(Committee's)* Explorer page:

* Cluster **balance in SSV**.
* **Total ETH** managed by a cluster.
* List of all validators managed by a cluster.

#### Validator's Explorer page:

* **Status** Active / Inactive.
* List of duties with **Operator Consensus Breakdown**. Breakdown has all of the steps performed by each member of the cluster for each duty.
* ETH balance of a validator.

## Troubleshooting low scores

* **Low proposal score:** Proposal duties are heavily weighted; missing them can notably reduce the total. Check proposer‑related participation in the details.
* **Leader assignment gaps:** Only one operator is leader in a round; if you weren’t the leader, those leader points simply don’t appear in your µ (you’re not “missing” them).
* **Quorum issues:** If rounds fail to finalize, ensure your **prepare/commit/pre‑consensus/post‑consensus** participation is healthy—you still earn credit for these.

Operators can check out [**Troubleshooting section**](/operators/operator-node/maintenance/troubleshooting.md) for more actionable steps on how to improve low scores.

## Calculations explained

You can find all used formulas on [this separate page](/learn/performance/calculations.md).