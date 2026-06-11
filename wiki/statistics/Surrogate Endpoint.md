---
title: "Surrogate Endpoint"
type: concept
status: learned
tags: [statistics, regulatory]
created: 2026-06-11
updated: 2026-06-11
sources: 1
---

# Surrogate Endpoint

A **surrogate endpoint (替代终点)** is a measure that stands in for the **true clinical endpoint** you actually care about (survival, symptoms, how a patient *feels / functions / survives*), used because it can be observed earlier or more easily. A biomarker or intermediate outcome becomes a surrogate when treatment decisions and approvals lean on it *instead of* the clinical outcome.

What makes something a surrogate is that it **substitutes for the clinical outcome** — not whether it is binary or continuous. A binary responder flag and a continuous biomarker can both be surrogates.

**Validity is the hard part.** For a surrogate to be trustworthy, the treatment's effect on the surrogate must *capture/explain* its effect on the true endpoint (the spirit of the **Prentice criteria**). Many plausible markers fail this: a drug can move the marker without improving survival (or vice versa). So a surrogate must be **validated**, not assumed.

Worked example — **[[PSA (Prostate-Specific Antigen)|PSA]] response (PSA50)** in prostate cancer:

- Used heavily because bone-predominant / [[Measurable vs Non-Measurable Disease (RECIST)|non-measurable disease]] makes RECIST ORR non-evaluable.
- A PSA decline only **correlates** with tumor-burden reduction — it does not measure tumor size, can fall disproportionately, and can show early "PSA flare". So it is an *indirect* readout.
- It is a **weak / not-fully-validated** surrogate for **OS**: PSA changes have repeatedly failed to reliably predict survival benefit. Regulators therefore don't accept PSA response alone; **rPFS** (radiographic progression-free survival) and **OS** carry the weight, and PCWG3 says report PSA but don't make it the primary efficacy basis.

Related: a surrogate that gets contaminated after the fact (e.g. by subsequent therapy) ties back to the [[Intercurrent Event]] / estimand framing.

