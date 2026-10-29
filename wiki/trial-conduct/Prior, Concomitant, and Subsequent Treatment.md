---
title: "Prior, Concomitant, and Subsequent Treatment"
type: concept
status: learned
created: 2026-06-19
---

# Prior, Concomitant, and Subsequent Treatment

It feels like many things, but it is really **two axes crossed** — not a long list. One axis = **type** (which SDTM domain); the other = **timing** (relative to the study treatment, **derived from dates**, *not* a separate domain).

## Axis 1 — type (= the domain)

- **Medication / drug** → **`CM`** (Concomitant/Prior Medications, 合并/既往用药) — all **non-study** drugs; coded with [[WHODrug]].
- **Procedure / surgery / radiotherapy / biopsy** → **`PR`** (Procedures, 操作/手术).
- The **study drug itself** → **`EX`** (Exposure, 暴露), **not** CM. CM = everything else.
- **"Anti-cancer therapy"** is *not* a separate domain — it is a **cut aimed at the cancer** that spans CM (systemic drugs) + PR (surgery / radiotherapy). See [[Anti-Cancer Therapy Categories in Oncology Trials]].

**Medication vs procedure vs therapy — different *levels*, not three parallel groups:**

- **Medication** = a **drug / substance** that is given (a compound, 化合物) → the *thing* is a chemical/biologic (`CM`).
- **Procedure** = an **action / intervention** done to the patient — surgery, radiotherapy, biopsy (`PR`); the *thing* is an act on the body.
- **Therapy** = an **umbrella** (总称) word for a **course of treatment** aimed at the disease — **delivered through** medications and/or procedures, not a recordable unit of its own. "First-line chemotherapy" is *one therapy* carried out as several drug administrations; "anti-cancer therapy" spans drugs (CM) + RT radiotherapy/surgery (PR).

So **medication and procedure are the concrete data units (atoms, 原子单位); therapy is the course/intent carried out through them.**

## Axis 2 — timing (relative to the study-treatment window)

Derived from dates compared with the `EX` window (a flag/derivation, **not** a new domain). The reference is the **whole treatment period**, *not* a single dose:

- **Prior** (既往) — started/stopped **before** the first study dose.
- **Concomitant** (合并) — taken **during** the treatment period (between the first and last dose) → "con meds". A medication between two study-drug doses is **concomitant, not subsequent**.
- **Post-treatment / Subsequent** (后续) — after the **whole treatment ends** (after the **last dose / EOT**, end of treatment), in follow-up. "Subsequent anti-cancer therapy" = the **next line** started after coming off the study drug (e.g. after progression). The exact cutoff (last dose, or +X days, or discontinuation date) is **defined in the SAP/protocol**.

## The grid (type × timing)

| Type ↓ \ Timing → | Prior | Concomitant | Subsequent |
|---|---|---|---|
| **Medication** (`CM`) | prior meds | con meds | subsequent meds |
| **Procedure** (`PR`) | prior surgery/RT/biopsy | on-study procedures | subsequent procedures |
| **Anti-cancer therapy** (CM+PR) | prior anti-cancer therapy | *(usually prohibited concurrently)* | subsequent anti-cancer therapy |

## Why each matters

- **Prior** therapy → **eligibility** (lines of prior treatment, washout 洗脱期), prognosis / stratification.
- **Concomitant** meds → **safety**, drug interactions, supportive care; checks for **prohibited medications**.
- **Subsequent / post-treatment** anti-cancer therapy → **confounds OS**; it is an **[[Intercurrent Event]]** (estimand handling / censoring decisions).

Key point: **"prior/concomitant/subsequent" is a timing relationship worked out from dates**; **"medication/procedure/therapy" is the type/domain.** Only ~2 domains (`CM`, `PR`) + `EX`, sliced by timing — that's why it feels like many things but isn't. These forms are on the [[eCRF Forms (Prostate Cancer Trial)|eCRF]]; a data concept used across [[Oncology]].
