---
title: "MTD and RP2D"
type: concept
status: learned
tags: [statistics, trial-conduct, medical]
created: 2026-06-18
updated: 2026-06-20
sources: 5
---

# MTD and RP2D

The two core outputs of Phase I oncology dose-finding (剂量探索).

- **MTD (Maximum Tolerated Dose, 最大耐受剂量)** — the highest dose with still-acceptable toxicity during dose escalation (剂量递增). Defined via **[[Dose-Limiting Toxicity (DLT)|DLT]]** (dose-limiting toxicity, 剂量限制性毒性), usually observed in the first treatment cycle; a 3+3 design or model-based method (CRM / BOIN) finds the highest dose keeping the DLT rate below a target (commonly ~33%).
- **RP2D (Recommended Phase 2 Dose, 推荐的二期剂量)** — the dose actually carried into Phase II. Historically RP2D = MTD ("higher is better" assumption). Now (esp. FDA **Project Optimus**) dose optimization (剂量优化) is emphasized: RP2D is often **below** MTD, chosen on efficacy, [[Pharmacokinetics (PK)|PK]]/exposure, target engagement (靶点占据), and long-term tolerability over multiple cycles — not just the maximum the patient can tolerate.

**In one line:** MTD is the *toxicity ceiling*; RP2D is the *dose actually recommended for use* — the two need not be equal.

## EWOC (Escalation With Overdose Control)

A Bayesian adaptive dose-finding design (贝叶斯自适应设计), in the same model-based family as CRM / BOIN, used to find the MTD.

- **Core idea** — at each step it estimates the posterior of the dose–toxicity curve (剂量-毒性曲线) and recommends the next dose, subject to a hard constraint: the posterior probability that the recommended dose **exceeds the true MTD** must not exceed a fixed **feasibility bound α** (可行性界限 α, e.g. 0.25). That constraint *is* the "overdose control" (超量控制).
- **vs CRM** — CRM symmetrically picks the dose with toxicity rate *closest* to target; EWOC is **asymmetric**: it explicitly penalizes overdosing, selecting the **α-quantile of the posterior MTD distribution** (后验 MTD 分布的 α 分位数) — more conservative about exceeding the MTD.
- α can be **relaxed (increased) as the trial proceeds**: conservative early to protect patients, faster approach to the MTD later.
- **MTD here is an unknown true parameter** (未知真值参数), not a known number — the model holds a *posterior distribution* (后验分布) over it. "Overdose" means falling to the right of that unknown true MTD, hence the probabilistic statement. As data accumulate the posterior narrows, so the dose can be pushed closer to the true MTD while still honoring the α constraint.

## A worked MTD definition (BLRM + EWOC)

A typical protocol wording: *"MTD = highest dose where the posterior probability of the true DLT rate being in the target interval [0.16–0.33] is above 0.50, with less than 25% risk of the true DLT rate being above 33%."* Unpacking it (Bayesian logistic regression model, **BLRM** 贝叶斯逻辑回归模型):

- **true DLT rate (真实 DLT 发生率)** — the unknown probability of a [[Dose-Limiting Toxicity (DLT)|DLT]] at that dose; the model holds a posterior over it.
- **target interval [0.16–0.33] (目标区间)** — splits the DLT-rate axis into under-dosing [0, 0.16), **target** [0.16, 0.33], and over-dosing (0.33, 1]. The target band is the "effective yet acceptably toxic" range.
- **"posterior probability … in the target interval … above 0.50"** — for a candidate dose, P(true DLT rate ∈ [0.16, 0.33] | data) > 0.50: more likely than not the dose's toxicity sits in the target window.
- **"less than 25% risk … above 33%"** — the **EWOC overdose-control** constraint: P(true DLT rate > 0.33 | data) < 0.25 (the α = 0.25 feasibility bound).
- **"highest dose where …"** — among doses meeting *both* conditions, the MTD is the **highest**.

So **MTD = highest dose with P(rate∈[0.16,0.33]) > 0.5 AND P(rate>0.33) < 0.25** — condition 1 keeps it in the target toxicity band, condition 2 keeps the overdose risk low.

## Optimal treatment regimen

A **treatment regimen (治疗方案)** is the complete *how* of giving a therapy: which drug(s), the **dose (剂量)**, **route (给药途径)**, **schedule/frequency (给药时间表/频率)**, cycle length, total duration, and any combination or sequence — not a single number, the whole plan.

- **Optimal treatment regimen (最优治疗方案)** — the regimen that best balances **efficacy (疗效)** and **safety/tolerability (安全性/耐受性)**, i.e. best **benefit-risk (获益-风险)** — *not necessarily* the maximum tolerated dose.
- This is the core idea of FDA **Project Optimus**: shift from the old "MTD = more is better" mindset toward deliberately choosing an optimal **dose AND schedule** before the pivotal trial. Ideally the **[[MTD and RP2D|RP2D]]** *is* the optimal regimen, not just the toxicity ceiling.
- Identified by comparing multiple dose/schedule arms on efficacy, [[Pharmacokinetics (PK)|PK]]/PD and exposure–response, safety, long-term tolerability over many cycles, and sometimes patient-reported outcomes.

Part of [[Oncology]].
