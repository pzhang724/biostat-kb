---
title: "MTD and RP2D"
type: concept
status: learned
tags: [statistics, trial-conduct, medical]
created: 2026-06-18
updated: 2026-06-18
sources: 3
---

# MTD and RP2D

The two core outputs of Phase I oncology dose-finding.

- **MTD (Maximum Tolerated Dose)** — the highest dose with still-acceptable toxicity during dose escalation. Defined via **DLT** (dose-limiting toxicity), usually observed in the first treatment cycle; a 3+3 design or model-based method (CRM / BOIN) finds the highest dose keeping the DLT rate below a target (commonly ~33%).
- **RP2D (Recommended Phase 2 Dose)** — the dose actually carried into Phase II. Historically RP2D = MTD ("higher is better" assumption). Now (esp. FDA **Project Optimus**) dose optimization is emphasized: RP2D is often **below** MTD, chosen on efficacy, [[Pharmacokinetics (PK)|PK]]/exposure, target engagement, and long-term tolerability over multiple cycles — not just the maximum the patient can tolerate.

**In one line:** MTD is the *toxicity ceiling*; RP2D is the *dose actually recommended for use* — the two need not be equal.

## EWOC (Escalation With Overdose Control)

A Bayesian adaptive dose-finding design, in the same model-based family as CRM / BOIN, used to find the MTD.

- **Core idea** — at each step it estimates the posterior of the dose–toxicity curve and recommends the next dose, subject to a hard constraint: the posterior probability that the recommended dose **exceeds the true MTD** must not exceed a fixed **feasibility bound α** (e.g. 0.25). That constraint *is* the "overdose control".
- **vs CRM** — CRM symmetrically picks the dose with toxicity rate *closest* to target; EWOC is **asymmetric**: it explicitly penalizes overdosing, selecting the **α-quantile of the posterior MTD distribution** — more conservative about exceeding the MTD.
- α can be **relaxed (increased) as the trial proceeds**: conservative early to protect patients, faster approach to the MTD later.
- **MTD here is an unknown true parameter**, not a known number — the model holds a *posterior distribution* over it. "Overdose" means falling to the right of that unknown true MTD, hence the probabilistic statement. As data accumulate the posterior narrows, so the dose can be pushed closer to the true MTD while still honoring the α constraint.

Part of [[Oncology]].
