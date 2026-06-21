---
title: "Simon's Two-Stage Design"
type: concept
status: learned
tags: [statistics]
created: 2026-06-20
updated: 2026-06-20
sources: 1
---

# Simon's Two-Stage Design

A **phase II, single-arm (单臂)** design for a **binary endpoint (二分类终点)** (response / no response — e.g. ORR from [[Best Overall Response]]) that screens whether a new agent has enough **[[Anti-Tumour Activity|anti-tumour activity]]** to pursue. Built-in **interim futility stop (期中无效终止)** so an inactive drug is abandoned early. (Typically follows phase I dose-finding — see [[MTD and RP2D]].)

- **Hypotheses** — **p₀** = response rate *not* worth pursuing (uninteresting), **p₁** = target rate of interest. Test **H₀: p ≤ p₀** vs **p ≥ p₁**, controlling **type I error α (一类错误)** and **power 1−β (检验效能)** at p₁.
- **Mechanics** (parameters **n₁, r₁, n, r**):
  - **Stage 1** — treat n₁ patients. If responses **≤ r₁ → STOP for futility** (not promising). Else continue.
  - **Stage 2** — treat up to total **n**. If total responses **≤ r → not promising**; **> r → promising** (worth further development).
  - Early stopping is **only for futility** (ethical: limit patients on an inactive drug); **no early efficacy stop**.

## Optimal vs minimax

Among *all* (n₁, r₁, n, r) meeting the α and power constraints, two standard picks:

- **Optimal** — minimizes the **expected sample size under the null, EN(p₀)** → stops early most often when the drug doesn't work.
- **Minimax** — minimizes the **maximum (total) sample size n** → smallest worst-case n.

**Minimax** is the choice when **accrual is slow / patients are scarce or expensive** and you want the smallest possible total n. Trade-off: minimax usually has a **larger n₁ and larger EN(p₀)** (stops early less often) than optimal; optimal has a smaller EN(p₀) but a larger maximum n. ("**Admissible**" designs compromise between the two.)

## Worked example

Computed for **p₀ = 0.10, p₁ = 0.30, α = 0.05, power = 0.80**:

| Design | Stage 1 (r₁/n₁) | Total (r/n) | EN(p₀) | P(stop early \| p₀) |
|---|---|---|---|---|
| Optimal | 1/10 | 5/29 | 15.0 | 74% |
| Minimax | 1/15 | 5/25 | 19.5 | 55% |

Read the minimax row: stop after stage 1 if ≤ 1 response in 15; otherwise go to 25 total and call the drug active only if > 5 responses. Minimax's **total n = 25 < optimal's 29** (smaller worst case), but it **expects more patients under the null** (19.5 vs 15.0) because it stops early less often.

Part of [[Oncology]]. See [[Best Overall Response]] (the ORR endpoint it tests), [[Anti-Tumour Activity]], [[MTD and RP2D]] (phase I that precedes it).
