---
title: "Surrogate Endpoint"
type: concept
status: learned
created: 2026-06-11
---

# Surrogate Endpoint

A **surrogate endpoint (替代终点)** is a measure that stands in for the **true clinical endpoint** you really care about (survival, symptoms, how a patient *feels / functions / survives*). It is used because it can be observed earlier or more easily. A biomarker or intermediate outcome (中间结局) becomes a surrogate when treatment decisions and approvals rely on it *instead of* the clinical outcome.

What makes something a surrogate is that it **replaces the clinical outcome** — not whether it is binary or continuous. A binary responder flag and a continuous biomarker can both be surrogates.

**Validity (有效性) is the hard part.** For a surrogate to be trustworthy, the treatment's effect on the surrogate must *capture/explain* its effect on the true endpoint (the spirit of the **Prentice criteria**, Prentice 准则). Many reasonable-looking markers fail this: a drug can move the marker without improving survival (or the other way round). So a surrogate must be **validated**, not assumed.

Worked example — **[[PSA (Prostate-Specific Antigen)|PSA]] response (PSA50)** in prostate cancer:

- Used a lot because disease that is mainly in bone / [[Measurable vs Non-Measurable Disease (RECIST)|non-measurable disease]] makes RECIST ORR impossible to evaluate.
- A fall in PSA only **correlates** with lower tumor burden — it does not measure tumor size, it can fall out of proportion (disproportionately), and it can show an early "PSA flare" (PSA 闪烁/一过性升高). So it is an *indirect* readout.
- It is a **weak / not fully validated** surrogate for **OS** (overall survival): PSA changes have failed again and again to reliably predict a survival benefit. So regulators don't accept PSA response alone; **rPFS** (radiographic progression-free survival) and **OS** carry the weight (see [[Progression-Free Survival (PFS) and Overall Survival (OS)]]), and PCWG3 says: report PSA, but don't make it the primary basis for efficacy.

Related: a surrogate that gets contaminated (污染) later on (e.g. by subsequent therapy) ties back to the [[Intercurrent Event]] / estimand framing.
