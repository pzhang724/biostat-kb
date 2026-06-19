---
title: "Prior, Concomitant, and Subsequent Treatment"
type: concept
status: learned
tags: [data-management, trial-conduct]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# Prior, Concomitant, and Subsequent Treatment

It feels like many things, but it's **two axes crossed** — not a long list. One axis = **type** (which SDTM domain); the other = **timing** (relative to study treatment, **derived from dates**, *not* a separate domain).

## Axis 1 — type (= the domain)

- **Medication / drug** → **`CM`** (Concomitant/Prior Medications) — all **non-study** drugs.
- **Procedure / surgery / radiotherapy / biopsy** → **`PR`** (Procedures).
- The **study drug itself** → **`EX`** (Exposure), **not** CM. CM = everything else.
- **"Anti-cancer therapy"** is *not* a separate domain — it's a **cancer-directed cut** spanning CM (systemic drugs) + PR (surgery / radiotherapy). See [[Anti-Cancer Therapy Categories in Oncology Trials]].

## Axis 2 — timing (relative to the study-treatment window)

Derived from dates vs the `EX` window (a flag/derivation, **not** a new domain):

- **Prior** — started/stopped **before** first study dose.
- **Concomitant** — taken **during** treatment (overlaps the study-drug window) → "con meds".
- **Post-treatment / Subsequent** — after last dose / in follow-up.

## The grid (type × timing)

| Type ↓ \ Timing → | Prior | Concomitant | Subsequent |
|---|---|---|---|
| **Medication** (`CM`) | prior meds | con meds | subsequent meds |
| **Procedure** (`PR`) | prior surgery/RT/biopsy | on-study procedures | subsequent procedures |
| **Anti-cancer therapy** (CM+PR) | prior anti-cancer therapy | *(usually prohibited concurrently)* | subsequent anti-cancer therapy |

## Why each matters

- **Prior** therapy → **eligibility** (lines of prior treatment, washout), prognosis / stratification.
- **Concomitant** meds → **safety**, drug interactions, supportive care; **prohibited-med** checks.
- **Subsequent / post** anti-cancer therapy → **confounds OS**; it's an **[[Intercurrent Event]]** (estimand handling / censoring decisions).

Key point: **"prior/concomitant/subsequent" is a timing relationship from dates**; **"medication/procedure/therapy" is the type/domain.** Only ~2 domains (`CM`, `PR`) + `EX`, sliced by timing — that's why it feels like many but isn't. These forms live on the [[eCRF Forms (Prostate Cancer Trial)|eCRF]]; a cross-cutting data concept in [[Oncology]].
