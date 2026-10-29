---
title: "Local (Investigator) vs Central (BICR) Tumour Assessment"
type: concept
status: learned
created: 2026-06-19
---

# Local (Investigator) vs Central (BICR) Tumour Assessment

**Lesion selection (病灶选择) happens once, at baseline**, by whoever reads the images. At later visits you **don't re-select** — you re-measure the **same** target lesions and look for new ones (see [[RECIST 1.1#Step 0 — Baseline lesion setup (TU + TR)|Step 0]]). But **who reads** can be two **parallel** readers:

## Local (investigator) read

The **site investigator** or the local radiologist (放射科医生) selects the target lesions at baseline, measures them at each visit, and assigns the response (`TREVAL`/`RSEVAL = INVESTIGATOR`). This drives **real-time clinical decisions** ([[Action Taken for an Adverse Event|treat / hold / stop]], next cycle). Fast, but it can be **biased** — the reader is not blinded (unblinded, 非盲) and is involved (invested) in the patient's care.

## Central read — BICR

**BICR** = Blinded Independent Central Review (独立中心盲态阅片). Images go to a **central imaging core lab** (中心影像实验室), where independent radiologists, **blinded** to the treatment arm and to the site's read, select **their own** target lesions and derive **their own** response (`= INDEPENDENT ASSESSOR`). Usually **2 readers + an adjudicator** (裁决者) for disagreements (discordance). It gives an **unbiased, standardized** efficacy readout.

## Where the difference lives

- **Who + where** — local = the treating investigator at the site; central = independent blinded radiologists at a core lab.
- **Purpose** — local drives patient management in real time; central gives the **unbiased endpoint for regulators**, especially when **ORR / [[Progression-Free Survival (PFS) and Overall Survival (OS)|PFS]]** is primary or key secondary in **open-label** (开放标签) trials, where the investigator's assessment of when progression happened is prone to bias.
- **Data** — `TREVAL`/`RSEVAL` (INVESTIGATOR vs INDEPENDENT ASSESSOR) separates the two **parallel** sets of records; they may pick different lesions and reach different responses. The **SAP** (statistical analysis plan, 统计分析计划) says which read drives the primary endpoint, and the **agreement between local and central** (concordance, 一致性) is itself analyzed.

## Two parallel TU/TR/RS sets — and where each comes from

- **Same domains, double the rows.** There are no separate central/local domains — the **same TU/TR/RS** (tumor identification / tumor results / response) hold both reads, told apart by the **evaluator** variable (`TUEVAL`/`TREVAL`/`RSEVAL` = INVESTIGATOR vs INDEPENDENT ASSESSOR). `--EVALID` further separates **several central readers** (Reader 1, Reader 2, Adjudicator). So one lesion can have an investigator TR row **and** an independent-assessor TR row.
- **They do NOT both go through the eCRF.** The **local/investigator** read → entered into the **eCRF/EDC** by the site (CRF data). The **central/BICR** read → a **non-CRF external feed** from the imaging core-lab vendor (like the central lab), loaded directly and reconciled (核对) — the site does **not** type it in. Both end up in the same SDTM TU/TR/RS, tagged by `--EVAL`. See [[CRF vs Non-CRF (External) Data]].
- **The scope can differ:** the investigator read is sometimes only the **overall response** (RS) on the eCRF, while the **BICR** vendor usually supplies the **full** TU/TR/RS (their own lesion selection + measurements + response) — a protocol/SAP decision.

The underlying imaging is [[Radiological Assessment]]; a concept about the integrity (完整性/可信度) of efficacy data, used across [[Oncology]].
