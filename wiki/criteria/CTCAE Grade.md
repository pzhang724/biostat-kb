---
title: "CTCAE Grade"
type: concept
status: learned
tags: [medical, regulatory, trial-conduct]
created: 2026-06-18
updated: 2026-06-19
sources: 4
---

# CTCAE Grade

**Common Terminology Criteria for Adverse Events** (不良事件通用术语标准分级) — NCI's standardized **severity grading** for adverse events.

- **Grade 1** — mild
- **Grade 2** — moderate
- **Grade 3** — severe / medically significant but not immediately life-threatening
- **Grade 4** — life-threatening, urgent intervention needed
- **Grade 5** — death related to the AE

Each AE term has its own term-specific grade definitions. Built on / maps to [[MedDRA]] terms.

Drives **safety summaries, dose modifications, and DLT definitions** (e.g. a grade ≥3 toxicity within cycle 1 — see [[MTD and RP2D]]). Lab toxicities on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]] are graded this way too.

## Why grade ≥3 gets the focus

**Grade 3 is the "severe" threshold** — the point where a toxicity is serious enough to require medical intervention, possibly hospitalization, and a dose change, with real impact on the patient. Grades 1–2 (mild/moderate) are mostly common, expected, and self-limited or easily managed, so they don't drive decisions. Hence ≥3 is what gets watched:

- It is the **action line** — dose reduction / interruption, treating the AE; in dose-finding it is essentially the [[Dose-Limiting Toxicity (DLT)|DLT]] threshold (≥3 non-hematologic / ≥4 hematologic).
- **Benefit-risk** (获益-风险) and regulatory/safety summaries focus on ≥3 — listing every grade-1 nausea is noise; severe events are what move benefit-risk.
- It is a **standardized, comparable cutoff** (via CTCAE), so "grade ≥3 rate" is a clean safety metric — tables often split *all grades* vs *grade ≥3*, the latter being the headline.

**In one line:** grade 3 is the line from "uncomfortable but tolerable" to "severe, must act" — so it governs dose changes, safety reporting, and toxicity comparisons.

## Grading lab tests — three cases

When grading a lab result (检验值) against CTCAE, a lab analyte maps to a CTCAE term in one of three ways:

- **One-sided / direct** — a single CTCAE term exists, e.g. ALT (谷丙转氨酶) → *Alanine aminotransferase increased*, AST (谷草转氨酶) → *Aspartate aminotransferase increased*. Look up the value, read off the grade.
- **Two-sided** — one analyte maps to **two** CTCAE terms, one per direction. E.g. calcium (钙, CA) → *Hypocalcemia* (低钙血症) and *Hypercalcemia* (高钙血症); which term applies depends on whether the value is below or above range.
- **No term** — some lab tests have **no** CTCAE record at all, e.g. the urine (尿) parameters in [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)|urinalysis]] — they cannot be CTCAE-graded.

### Handling the no-term case

A parameter with no CTCAE term simply gets **no grade** — don't force one. In ADaM **ADLB** the toxicity-grade variable (`ATOXGR` / `ATOXGRL` / `ATOXGRH`) is left **null** for it. You still analyze the value, just by **reference-range flag** instead of grade — `LBNRIND` NORMAL / LOW / HIGH, shift tables, and the investigator's clinically-significant flag. If an abnormal ungraded lab is genuinely clinically significant, the investigator records it as an **adverse event** (AE domain); that AE term then carries its own CTCAE grade — the grade lives on the reported AE, not derived from the lab value. (Note: calcium *does* have terms — *Hypocalcemia* / *Hypercalcemia*; the real no-term case is things like urinalysis.)

Distinct from an [[Adverse Event of Special Interest (AESI)]] (interest-based pre-specified watch) — AESIs are still graded with CTCAE. A cross-cutting grading standard in [[Oncology]].
