---
title: "Local (Investigator) vs Central (BICR) Tumour Assessment"
type: concept
status: learned
tags: [trial-conduct, statistics]
created: 2026-06-19
updated: 2026-06-19
sources: 2
---

# Local (Investigator) vs Central (BICR) Tumour Assessment

**Lesion selection happens once at baseline**, by whoever reads the images — at later visits you **don't re-select**, you re-measure the **same** target lesions and look for new ones (see [[RECIST 1.1#Step 0 — Baseline lesion setup (TU + TR) — four sub-steps, all fixed at baseline|Step 0]]). But **who reads** can be two **parallel** readers:

## Local (investigator) read

The **site investigator** or local radiologist selects target lesions at baseline, measures them each visit, and assigns the response (`TREVAL`/`RSEVAL = INVESTIGATOR`). Drives **real-time clinical decisions** ([[Action Taken for an Adverse Event|treat / hold / stop]], next cycle). Fast, but potentially **biased** — the reader is unblinded and invested in the patient.

## Central read — BICR

**BICR** = Blinded Independent Central Review. Images go to a **central imaging core lab** where independent radiologists, **blinded** to treatment arm and to the site's read, select **their own** target lesions and derive **their own** response (`= INDEPENDENT ASSESSOR`). Usually **2 readers + an adjudicator** for discordance. Gives an **unbiased, standardized** efficacy readout.

## Where the difference lives

- **Who + where** — local = treating investigator at the site; central = independent blinded radiologists at a core lab.
- **Purpose** — local drives patient management in real time; central provides the **unbiased endpoint for regulators**, especially **ORR / [[Progression-Free Survival (PFS) and Overall Survival (OS)|PFS]]** as primary or key secondary in **open-label** trials, where investigator assessment of progression timing is bias-prone.
- **Data** — `TREVAL`/`RSEVAL` (INVESTIGATOR vs INDEPENDENT ASSESSOR) distinguishes the two **parallel** record sets; they may pick different lesions and reach different responses. The **SAP** says which read drives the primary endpoint, and **local-vs-central concordance** is itself analyzed.

## Two parallel TU/TR/RS sets — and where each comes from

- **Same domains, doubled rows.** There aren't separate central/local domains — the **same TU/TR/RS** hold both reads, distinguished by the **evaluator** variable (`TUEVAL`/`TREVAL`/`RSEVAL` = INVESTIGATOR vs INDEPENDENT ASSESSOR). `--EVALID` further separates **multiple central readers** (Reader 1, Reader 2, Adjudicator). So one lesion can have an investigator TR row **and** an independent-assessor TR row.
- **They do NOT both go through the eCRF.** **Local/investigator** read → entered into the **eCRF/EDC** by the site (CRF data). **Central/BICR** read → a **non-CRF external feed** from the imaging core-lab vendor (like central lab), loaded directly + reconciled — the site does **not** key it in. Both converge into the same SDTM TU/TR/RS, tagged by `--EVAL`. See [[CRF vs Non-CRF (External) Data]].
- **Scope can differ:** the investigator read is sometimes only the **overall response** (RS) on the eCRF, while the **BICR** vendor usually supplies **full** TU/TR/RS (their own lesion selection + measurements + response) — a protocol/SAP decision.

The underlying imaging is [[Radiological Assessment]]; a cross-cutting efficacy-integrity concept in [[Oncology]].
