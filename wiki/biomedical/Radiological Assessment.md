---
title: "Radiological Assessment"
type: concept
status: learned
tags: [medical, trial-conduct]
created: 2026-06-18
updated: 2026-06-18
sources: 4
---

# Radiological Assessment

**Radiological assessment (影像学评估)** — evaluating disease with medical **imaging** (CT, MRI, bone scan, [[PSMA PET-CT]], etc.): measuring tumour burden, detecting/measuring lesions, and judging response or progression. In oncology trials it is the imaging-based read of disease status that **feeds the response criteria** ([[RECIST 1.1]], [[PCWG3 Criteria]], the [[Modified RECIST 1.1 and PCWG3 Criteria]]) → [[Best Overall Response|overall response]], progression, rPFS.

- One of three assessment types — distinct from **clinical** (symptoms/exam) and **lab / biomarker** assessment (e.g. [[PSA (Prostate-Specific Antigen)|PSA]]). Radiological means imaging specifically.
- Performed at protocol-scheduled timepoints (scan schedule).
- Often read by **BICR** (blinded independent central review, 独立中心盲态阅片) rather than only the local investigator, to reduce bias.
- **Radiological progression (影像学进展)** is the imaging-defined progression event — the basis of **rPFS** (radiographic progression-free survival).

**Why one criterion still gives different reads** — the standard is a rule, but applying it needs human **judgment calls** that aren't fully deterministic, so the same rule read by different people varies. In tumour imaging (RECIST): which lesions to pick as **target lesions** (up to 5), where to draw the diameter (which slice, caliper placement, partial-volume effect), and whether something is a **new lesion** or **progression** at the borderline (~20% growth, image quality, artifact). In **ECG/QTc**: where to place the **T-wave offset** (notoriously reader-dependent), manual vs algorithm, which leads/beats, baseline noise. On top of this **variability** there is **bias** — a local reader is often unblinded (knows the arm, has real-time treatment incentives), whereas central is blinded, standardized, and works from the complete dataset. **This applies wherever a human read/measurement sits between raw data and the categorical result** — tumour imaging, ECG, also central pathology, bone scans, echo, photographs; the more objective/automated the measure, the smaller the gap.

**When local and central disagree** — discordance is common and expected. Note it is **one criterion, two independent reads** (local and central apply the *same* rules, e.g. RECIST 1.1 / the same QTc threshold — what differs is *who reads*), not two competing standards. Both coexist in the dataset; the protocol pre-specifies which is primary, and the two serve different purposes:

- **Patient management follows local** — treatment / stopping and real-time safety can't wait for central, so the site read drives care.
- **The statistical analysis follows central** — regulated efficacy/safety endpoints (progression, rPFS, QTc) use the blinded central read as the primary analysis, for cross-site consistency and less bias.
- Discordance is **quantified and managed**: BICR often uses **two independent readers + a third adjudicator** (adjudication, 裁决); the **discordance rate** is examined; systematic bias (e.g. evaluation-time bias from coming off treatment on the local read) is checked with **sensitivity analyses** and censoring rules.
- A large discordance is mainly a **bias / credibility** signal, not just a data-quality issue: central reading partly exists to **audit the local read for bias** (esp. open-label, where the investigator knows the arm). Agreement → reassurance; big systematic divergence → trust central (primary) and investigate why (which *may* include reader-quality / retraining, but the core question is the endpoint's credibility).

**In one line:** not "who's right" — local decides how the patient is treated, central decides how the data are counted; the protocol names the primary (usually central) and stress-tests disagreement.

What it measures comes from [[Measurable vs Non-Measurable Disease (RECIST)|measurability rules]]. A cross-cutting assessment in [[Oncology]].
