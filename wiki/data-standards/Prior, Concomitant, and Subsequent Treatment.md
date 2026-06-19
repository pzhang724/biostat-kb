---
title: "Prior, Concomitant, and Subsequent Treatment"
type: concept
status: learned
tags: [data-management, trial-conduct]
created: 2026-06-19
updated: 2026-06-19
sources: 2
---

# Prior, Concomitant, and Subsequent Treatment

It feels like many things, but it's **two axes crossed** — not a long list. One axis = **type** (which SDTM domain); the other = **timing** (relative to study treatment, **derived from dates**, *not* a separate domain).

## Axis 1 — type (= the domain)

- **Medication / drug** → **`CM`** (Concomitant/Prior Medications) — all **non-study** drugs; coded with [[WHODrug]].
- **Procedure / surgery / radiotherapy / biopsy** → **`PR`** (Procedures).
- The **study drug itself** → **`EX`** (Exposure), **not** CM. CM = everything else.
- **"Anti-cancer therapy"** is *not* a separate domain — it's a **cancer-directed cut** spanning CM (systemic drugs) + PR (surgery / radiotherapy). See [[Anti-Cancer Therapy Categories in Oncology Trials]].

**Medication vs procedure vs therapy — different *levels*, not three parallel buckets:**

- **Medication** = a **drug / substance** given (a compound) → the *thing* is a chemical/biologic (`CM`).
- **Procedure** = an **action / intervention** done to the patient — surgery, radiotherapy, biopsy (`PR`); the *thing* is an act on the body.
- **Therapy** = an **umbrella** word for a **course of treatment** aimed at the disease — **delivered through** medications and/or procedures, not a recordable atom of its own. "First-line chemotherapy" is *one therapy* realized as several drug administrations; "anti-cancer therapy" spans drugs (CM) + RT/surgery (PR).

So **medication & procedure are the concrete data atoms; therapy is the course/intent realized through them.**

## Axis 2 — timing (relative to the study-treatment window)

Derived from dates vs the `EX` window (a flag/derivation, **not** a new domain). The reference is the **whole treatment period**, *not* a single dose:

- **Prior** — started/stopped **before** first study dose.
- **Concomitant** — taken **during** the treatment period (between first and last dose) → "con meds". A med between two study-drug doses is **concomitant, not subsequent**.
- **Post-treatment / Subsequent** — after the **whole treatment ends** (after the **last dose / EOT**), in follow-up. "Subsequent anti-cancer therapy" = the **next line** started after coming off study drug (e.g. after progression). Exact cutoff (last dose, or +X days, or discontinuation date) is **SAP/protocol-defined**.

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
