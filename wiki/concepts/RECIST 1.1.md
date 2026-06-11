---
title: "RECIST 1.1"
type: concept
status: learned
tags: [medical, statistics, standards]
created: 2026-06-11
updated: 2026-06-11
sources: 2
---

# RECIST 1.1

**RECIST 1.1** (Response Evaluation Criteria In Solid Tumors, version 1.1, 2009) is the standardized, imaging-based rule set for assessing solid-tumor response — the common language behind ORR / PFS / DoR in solid-tumor trials.

**Setup:**

- **Measurable lesion** — longest diameter ≥10 mm on CT/MRI (lymph node measured by **short axis** ≥15 mm). See [[Measurable vs Non-Measurable Disease (RECIST)]].
- **Target lesions** — up to **5 total, max 2 per organ**; record the **sum of diameters (SoD)** (nodes contribute short axis). Everything else is a **non-target** lesion, assessed qualitatively.

**Response categories** (overall response integrates target + non-target + new lesions):

- **CR (complete response)** — all target lesions gone; any lymph nodes <10 mm short axis.
- **PR (partial response)** — ≥30% decrease in SoD vs baseline.
- **PD (progressive disease)** — ≥20% increase in SoD vs the nadir (smallest SoD so far) **and** ≥5 mm absolute increase; **or** any new lesion; **or** unequivocal non-target progression.
- **SD (stable disease)** — neither PR nor PD.

CR/PR usually require **confirmation** (repeat scan ≥4 weeks later) in ORR-primary or non-randomized trials. Derived endpoints: **ORR, DoR, PFS**.

## Overall response — all combinations

The time-point **overall response** combines target, non-target, and new-lesion status. Rule of thumb: **progression in any one channel → overall PD**, and **CR requires CR everywhere with no new lesions**.

Patients **with target lesions**:

| Target | Non-target | New lesions | Overall |
|--------|-----------|-------------|---------|
| CR | CR | No | **CR** |
| CR | Non-CR/Non-PD | No | **PR** |
| CR | NE | No | **PR** |
| PR | Non-PD or NE | No | **PR** |
| SD | Non-PD or NE | No | **SD** |
| NE | Non-PD | No | **NE** |
| PD | Any | Yes or No | **PD** |
| Any | PD | Yes or No | **PD** |
| Any | Any | Yes | **PD** |

Patients with **non-target disease only** (no measurable target) — note "Non-CR/Non-PD" replaces "SD":

| Non-target | New lesions | Overall |
|-----------|-------------|---------|
| CR | No | **CR** |
| Non-CR/Non-PD | No | **Non-CR/Non-PD** |
| NE | No | **NE** |
| Unequivocal PD | Yes or No | **PD** |
| Any | Yes | **PD** |

(CR = complete response, PR = partial response, SD = stable disease, PD = progressive disease, NE = not evaluable.)

In a [[PCWG3 Criteria]] mCRPC trial these RECIST calls cover only the **soft-tissue/nodal** channel; bone is judged separately by the 2+2 rule, and the two are fused into the single composite criterion [[Modified RECIST 1.1 and PCWG3 Criteria]] that defines rPFS.

Limitation that motivates [[PCWG3 Criteria]]: RECIST needs measurable disease, so it can't properly assess **bone-predominant** prostate cancer — hence the prostate-specific bone/PSA rules. See also [[PSA (Prostate-Specific Antigen)]].

## Official reference

Eisenhauer EA, Therasse P, Bogaerts J, et al. **New response evaluation criteria in solid tumours: revised RECIST guideline (version 1.1).** *Eur J Cancer.* 2009;45(2):228–247. doi:10.1016/j.ejca.2008.10.026

Sources: [[RECIST 1.1 and PCWG3 (chat)]] · [[RECIST overall response combinations (chat)]]
