---
title: "Progression-Free Survival (PFS) and Overall Survival (OS)"
type: concept
status: learned
tags: [statistics, medical]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# Progression-Free Survival (PFS) and Overall Survival (OS)

The two main **time-to-event** (survival) efficacy endpoints in oncology — distinct from the **response-based** endpoints (ORR, DCR, DoR) that derive from [[Best Overall Response]].

## PFS — Progression-Free Survival (无进展生存)

Time from **randomization** to **first PD or death from any cause, whichever comes first**; patients with neither event are **censored**. Captures **delay of progression**.

- Reads out **earlier** than OS — you don't wait for deaths.
- **Caveats:** depends on the **assessment schedule** ([[Schedule of Assessments|SoA]]) → interval censoring + evaluation-time bias; needs **blinded independent central review (BICR)** to limit ascertainment bias; censoring rules depend on the **estimand** (a subsequent therapy is an [[Intercurrent Event]]). Progression is defined by [[RECIST 1.1]] / [[PCWG3 Criteria]]; the radiographic version **rPFS** is used in prostate cancer.

## OS — Overall Survival (总生存)

Time from **randomization** to **death from any cause**. The **gold-standard true endpoint** — objective, unambiguous, **not** assessment-dependent.

- **Caveats:** needs **long follow-up** and many death events, large sample; **confounded / diluted** by subsequent therapies and crossover.

## How they relate

OS is the true **clinical benefit**; **ORR / DoR / DCR / PFS** are **earlier readouts** that act as [[Surrogate Endpoint|surrogate endpoints]] for OS (PFS validated in some tumours, not all). This is the [[Anti-Tumour Activity|activity]] → clinical-benefit ladder. A cross-cutting efficacy concept in [[Oncology]].
