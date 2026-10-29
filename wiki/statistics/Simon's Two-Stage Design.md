---
title: "Simon's Two-Stage Design"
type: concept
status: learned
created: 2026-06-20
---

# Simon's Two-Stage Design

A **phase II, single-arm (单臂)** design for a **binary endpoint (二分类终点)** (response / no response — e.g. ORR from [[Best Overall Response]]). It screens whether a new drug has enough **[[Anti-Tumour Activity|anti-tumour activity]]** to continue with. It has a built-in **interim stop for futility (期中无效终止)**, so an inactive drug is dropped early. (It usually comes after phase I dose-finding — see [[MTD and RP2D]].)

- **Hypotheses** — **p₀** = a response rate *not* worth pursuing (uninteresting); **p₁** = the target rate of interest. Test **H₀: p ≤ p₀** vs **p ≥ p₁**, controlling the **type I error α (一类错误)** and the **power 1−β (检验效能)** at p₁.
- **Mechanics** (parameters **n₁, r₁, n, r**):
  - **Stage 1** — treat n₁ patients. If responses are **≤ r₁ → STOP for futility** (not promising). Otherwise continue.
  - **Stage 2** — treat up to **n** in total. If total responses are **≤ r → not promising**; **> r → promising** (worth further development).
  - The early stop is **only for futility** (ethical reason: limit the number of patients on an inactive drug); there is **no early stop for efficacy**.

## Optimal vs minimax

Among *all* (n₁, r₁, n, r) that meet the α and power limits, there are two standard choices:

- **Optimal** (最优设计) — minimizes the **expected sample size under the null, EN(p₀)** → it stops early most often when the drug doesn't work.
- **Minimax** (极小极大设计) — minimizes the **maximum (total) sample size n** → the smallest worst-case n.

**Minimax** is the choice when **enrollment (accrual, 入组) is slow / patients are scarce or expensive** and you want the smallest possible total n. Trade-off: minimax usually has a **larger n₁ and a larger EN(p₀)** (it stops early less often) than optimal; optimal has a smaller EN(p₀) but a larger maximum n. ("**Admissible**" designs, 可容许设计, are a compromise between the two.)

## Worked example

Computed for **p₀ = 0.10, p₁ = 0.30, α = 0.05, power = 0.80**:

| Design | Stage 1 (r₁/n₁) | Total (r/n) | EN(p₀) | P(stop early \| p₀) |
|---|---|---|---|---|
| Optimal | 1/10 | 5/29 | 15.0 | 74% |
| Minimax | 1/15 | 5/25 | 19.5 | 55% |

How to read the minimax row: stop after stage 1 if there is ≤ 1 response in 15; otherwise go to 25 in total, and call the drug active only if there are > 5 responses. Minimax's **total n = 25 < optimal's 29** (a smaller worst case), but it **expects more patients under the null** (19.5 vs 15.0) because it stops early less often.

Part of [[Oncology]]. See [[Best Overall Response]] (the ORR endpoint it tests), [[Anti-Tumour Activity]], [[MTD and RP2D]] (the phase I that comes before it).
