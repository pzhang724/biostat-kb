---
title: "MTD and RP2D"
type: concept
status: learned
created: 2026-06-18
---

# MTD and RP2D

The two core outputs of Phase I dose-finding (剂量探索) in oncology.

- **MTD (Maximum Tolerated Dose, 最大耐受剂量)** — the highest dose whose toxicity is still acceptable during dose escalation (剂量递增). Defined through **[[Dose-Limiting Toxicity (DLT)|DLT]]** (dose-limiting toxicity, 剂量限制性毒性), usually observed in the first treatment cycle. A 3+3 design or a model-based method (CRM, continual reassessment method; BOIN) finds the highest dose that keeps the DLT rate below a target (commonly ~33%).
- **RP2D (Recommended Phase 2 Dose, 推荐的二期剂量)** — the dose actually taken forward into Phase II. In the past RP2D = MTD (the "higher is better" assumption). Now (especially with FDA **Project Optimus**) dose optimization (剂量优化) is stressed: RP2D is often **below** the MTD, chosen on efficacy, [[Pharmacokinetics (PK)|PK]]/exposure, target engagement (靶点占据), and long-term tolerability over many cycles — not just the maximum the patient can tolerate.

**In one line:** the MTD is the *toxicity ceiling*; the RP2D is the *dose actually recommended for use* — the two do not have to be equal.

## EWOC (Escalation With Overdose Control)

A Bayesian adaptive dose-finding design (贝叶斯自适应设计), in the same model-based family as CRM / BOIN, used to find the MTD.

- **Core idea** — at each step it estimates the posterior (后验) of the dose–toxicity curve (剂量-毒性曲线) and recommends the next dose, under a hard rule: the posterior probability that the recommended dose **is above the true MTD** must not exceed a fixed **feasibility bound α** (可行性界限 α, e.g. 0.25). That rule *is* the "overdose control" (超量控制).
- **vs CRM** — CRM symmetrically picks the dose whose toxicity rate is *closest* to the target; EWOC is **asymmetric** (不对称): it clearly penalizes overdosing, choosing the **α-quantile of the posterior MTD distribution** (后验 MTD 分布的 α 分位数) — more careful about going above the MTD.
- α can be **relaxed (raised) as the trial goes on**: careful early on to protect patients, then a faster approach to the MTD later.
- **The MTD here is an unknown true parameter** (未知真值参数), not a known number — the model holds a *posterior distribution* (后验分布) over it. "Overdose" means falling to the right of that unknown true MTD; that's why the statement is about probability. As data build up, the posterior gets narrower, so the dose can be pushed closer to the true MTD while still keeping to the α rule.

## A worked MTD definition (BLRM + EWOC)

A typical protocol wording: *"MTD = highest dose where the posterior probability of the true DLT rate being in the target interval [0.16–0.33] is above 0.50, with less than 25% risk of the true DLT rate being above 33%."* Unpacking it (Bayesian logistic regression model, **BLRM**, 贝叶斯逻辑回归模型):

- **true DLT rate (真实 DLT 发生率)** — the unknown probability of a [[Dose-Limiting Toxicity (DLT)|DLT]] at that dose; the model holds a posterior over it.
- **target interval [0.16–0.33] (目标区间)** — splits the DLT-rate axis into under-dosing [0, 0.16), **target** [0.16, 0.33], and over-dosing (0.33, 1]. The target band is the "effective, and acceptably toxic" range.
- **"posterior probability … in the target interval … above 0.50"** — for a candidate dose, P(true DLT rate ∈ [0.16, 0.33] | data) > 0.50: it is more likely than not that the dose's toxicity is in the target window.
- **"less than 25% risk … above 33%"** — the **EWOC overdose-control** rule: P(true DLT rate > 0.33 | data) < 0.25 (the α = 0.25 feasibility bound).
- **"highest dose where …"** — among the doses that meet *both* conditions, the MTD is the **highest**.

So **MTD = the highest dose with P(rate∈[0.16,0.33]) > 0.5 AND P(rate>0.33) < 0.25** — condition 1 keeps it in the target toxicity band; condition 2 keeps the overdose risk low.

## Optimal treatment regimen

A **treatment regimen (治疗方案)** is the complete *how* of giving a therapy: which drug(s), the **dose (剂量)**, the **route (给药途径)**, the **schedule/frequency (给药时间表/频率)**, cycle length, total duration, and any combination or sequence — not a single number, but the whole plan.

- **Optimal treatment regimen (最优治疗方案)** — the regimen with the best balance of **efficacy (疗效)** and **safety/tolerability (安全性/耐受性)**, i.e. the best **benefit-risk (获益-风险)** — *not necessarily* the maximum tolerated dose.
- This is the core idea of FDA **Project Optimus**: move away from the old "MTD = more is better" thinking, towards choosing an optimal **dose AND schedule** on purpose before the pivotal (关键性) trial. Ideally the **[[MTD and RP2D|RP2D]]** *is* the optimal regimen, not just the toxicity ceiling.
- Found by comparing several dose/schedule arms on efficacy, [[Pharmacokinetics (PK)|PK]]/PD (pharmacodynamics, 药效学) and exposure–response, safety, long-term tolerability over many cycles, and sometimes patient-reported outcomes.

## BOIN (Bayesian Optimal Interval) design

A phase I dose-finding design (剂量探索设计) to find the MTD, in the **model-assisted (模型辅助)** family — it sits *between* algorithm-based designs (3+3) and fully model-based designs ([[#EWOC (Escalation With Overdose Control)|EWOC]] / CRM).

- **Core rule (interval-based up-and-down)** — set a **target DLT rate φ (目标 DLT 发生率)** in advance (e.g. 0.25). From φ, two **fixed boundaries** are derived: **λ_e (escalation, 递增边界)** and **λ_d (de-escalation, 递减边界)** (for φ=0.25, ≈ 0.197 and 0.298). At the current dose, compute the observed rate **p̂ = #DLTs / #patients**, then:
  - **p̂ ≤ λ_e → escalate** to the next higher dose;
  - **p̂ ≥ λ_d → de-escalate**;
  - **in between → stay** at the current dose.
  Plus a safety rule to drop doses that are too toxic. The interval is called "**optimal**" because λ_e and λ_d are derived to **minimize the probability of wrong escalation/de-escalation decisions**.
- **Why it is attractive** — it combines the **simplicity/transparency** (透明) of algorithm-based designs (decisions can be **listed in a table beforehand** that the team follows; no real-time modelling or software while the trial runs) with **operating characteristics (操作特性) comparable to CRM**. Each decision depends only on the current dose's data, φ, and the fixed boundaries.
- **vs 3+3** — it targets a *specified* DLT rate, allows any cohort size, and has better operating characteristics. **vs CRM/[[#EWOC (Escalation With Overdose Control)|EWOC]]** — those fit/update a dose-toxicity curve all the time (model-based); BOIN is *model-assisted* — a likelihood/Bayesian argument produces the boundaries, but the trial rule is a plain interval comparison, with **no curve fitting**.
- **MTD selection at the end** — after stopping (maximum sample size, etc.), estimate the toxicity rates by **isotonic regression (保序回归)** and pick the dose whose rate is closest to φ.
- **Extensions** — **TITE-BOIN** (time-to-event; handles **late-onset toxicity (迟发毒性)** — relevant for long/delayed toxicities like those of [[Radiopharmaceutical Therapy (RPT) and External Beam Radiation Therapy (EBRT)|radioligands]]); **BOIN12** (utility-based, 效用; uses toxicity + efficacy together for **dose optimization** — see [[#Optimal treatment regimen]], Project Optimus); drug-combination BOIN.

### Run it off a table — no live modeling

The defining practical feature: **the whole escalation runs from one table computed beforehand — no real-time modelling.**

- **λ_e and λ_d are computed once**, before the trial, from φ alone — they do **not** depend on the data as it comes in.
- From them you print a **decision table (决策表)**, indexed by the *number of patients treated at the current dose*: for each N it says "escalate if #DLT ≤ a / de-escalate if #DLT ≥ b / otherwise stay."
- **While the trial runs**, every decision = look up the current dose's row, compare the DLT count, and move. Simple arithmetic anyone can do — **no statistician at the bedside, no software, no re-fitting of the curve** after each cohort.
- **Compare CRM/EWOC** — those re-fit/update the dose-toxicity curve after *every* cohort (software + statistician in the loop) to get the next dose. BOIN puts all the thinking into the table up front.
- The **only** modelling-like step in BOIN is a **one-time isotonic regression at the very end** to pick the MTD — not during escalation.

Decision table computed beforehand (φ = 0.25):

| N at current dose | escalate if #DLT ≤ | de-escalate if #DLT ≥ | otherwise |
|---|---|---|---|
| 3 | 0 | 1 | stay |
| 6 | 1 | 2 | stay |
| 9 | 1 | 3 | stay |
| 12 | 2 | 4 | stay |

### Worked example

Cohort size 3, doses D1 < D2 < D3, target φ = 0.25 — every step is just a table lookup:

| Cohort | Dose | DLT this cohort | Running at dose | Table says | Move |
|---|---|---|---|---|---|
| 1 | D1 | 0 | 0/3 | 0 ≤ 0 | escalate → D2 |
| 2 | D2 | 0 | 0/3 | 0 ≤ 0 | escalate → D3 |
| 3 | D3 | 2 | 2/3 | 2 ≥ 1 | de-escalate → D2 |
| 4 | D2 | 1 | 1/6 | 1 ≤ 1 | escalate → D3 |
| 5 | D3 | 1 | 3/6 | 3 ≥ 2 | de-escalate → D2 |
| 6 | D2 | 1 | 2/9 | = 2 | **stay** → stop (max N) |

Final: D1 0/3 (0%), **D2 2/9 (~22%)**, D3 3/6 (50%). **MTD = the dose with the rate closest to φ and not over it → D2** (~22%, closest to 25%). Every move was a lookup; the only computation was the single MTD selection at the end of the trial.

Part of [[Oncology]].
