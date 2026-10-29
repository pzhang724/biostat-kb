---
title: "CTCAE Grade"
type: concept
status: learned
created: 2026-06-18
---

# CTCAE Grade

**Common Terminology Criteria for Adverse Events** (CTCAE, 不良事件通用术语标准) — the standard **severity grading** (严重程度分级) for adverse events, from the NCI (National Cancer Institute, 美国国家癌症研究所).

- **Grade 1** — mild (轻度)
- **Grade 2** — moderate (中度)
- **Grade 3** — severe (重度) / medically significant, but not immediately life-threatening
- **Grade 4** — life-threatening; urgent intervention (干预) needed
- **Grade 5** — death related to the AE

Each AE term has its own grade definitions. Built on / maps to [[MedDRA]] terms.

Drives **safety summaries, dose changes (dose modifications), and DLT definitions** (e.g. a grade ≥3 toxicity in cycle 1 — see [[MTD and RP2D]]). Lab toxicities on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]] are graded this way too.

## Why grade ≥3 gets the focus

**Grade 3 is the "severe" threshold** — the point where a toxicity is serious enough to need medical treatment (intervention), maybe hospitalization (住院), and a dose change, with a real impact on the patient. Grades 1–2 (mild/moderate) are mostly common and expected, and they go away by themselves (self-limited, 自限性) or are easy to manage, so they don't drive decisions. That's why ≥3 is what gets watched:

- It is the **action line** — dose reduction / interruption (暂停), treating the AE. In dose-finding it is basically the [[Dose-Limiting Toxicity (DLT)|DLT]] threshold (≥3 non-hematologic / ≥4 hematologic).
- **Benefit-risk** (获益-风险) and regulatory/safety summaries focus on ≥3 — listing every grade-1 nausea is noise; severe events are what change the benefit-risk balance.
- It is a **standard, comparable cutoff** (界值) (via CTCAE), so "grade ≥3 rate" is a clean safety metric. Tables often split *all grades* vs *grade ≥3*, and the latter is the headline (重点).

**In one line:** grade 3 is the line from "uncomfortable but tolerable" (可耐受) to "severe, must act" — so it controls dose changes, safety reporting, and comparisons of toxicity.

## Grading lab tests — three cases

When you grade a lab result (检验值) with CTCAE, a lab analyte (检测项目) maps to a CTCAE term in one of three ways:

- **One-sided / direct** — there is a single CTCAE term, e.g. ALT (谷丙转氨酶) → *Alanine aminotransferase increased*, AST (谷草转氨酶) → *Aspartate aminotransferase increased*. Look up the value and read off the grade.
- **Two-sided** — one analyte maps to **two** CTCAE terms, one for each direction. E.g. calcium (钙, CA) → *Hypocalcemia* (低钙血症) and *Hypercalcemia* (高钙血症); which term applies depends on whether the value is below or above the range.
- **No term** — some lab tests have **no** CTCAE entry at all, e.g. the urine (尿) parameters in [[Laboratory Safety Panels (Hematology, Chemistry, Coagulation, Urinalysis)|urinalysis]] — they cannot be CTCAE-graded.

### Handling the no-term case

A parameter with no CTCAE term simply gets **no grade** — don't force one. In ADaM **ADLB** the toxicity-grade variable (`ATOXGR` / `ATOXGRL` / `ATOXGRH`) is left **null** (空) for it. You still analyze the value, just by **reference-range flag** (参考范围标记) instead of grade — `LBNRIND` NORMAL / LOW / HIGH, shift tables (转换表), and the investigator's clinically-significant flag (临床意义标记). If an abnormal lab with no grade is really clinically significant, the investigator records it as an **adverse event** (AE domain); that AE term then has its own CTCAE grade — the grade lives on the reported AE, not derived from the lab value. (Note: calcium *does* have terms — *Hypocalcemia* / *Hypercalcemia*; the real no-term case is things like urinalysis.)

## Is CTCAE only on central-lab data?

**No** — CTCAE grades *adverse events*, and AEs come by two routes; only one of them is the central lab:

- **Clinical / symptomatic AEs** — graded by the **investigator at the site** (nausea 恶心, fatigue 乏力, pain 疼痛…) and entered in the AE eCRF (electronic case report form, 电子病例报告表; CRF data). Independent of any lab. This is **most** of the CTCAE grading.
- **Lab-derived toxicity grades** — here the central lab is the natural source: the value maps to its CTCAE term/threshold → `ATOXGR` in ADaM **ADLB**, usually **derived by a program in ADaM** from the value (some central labs also deliver the grade/flag in the data feed).

Why the central lab *feels* like the CTCAE source: it gives one standard assay (检测方法) + reference range + a full numeric panel across all sites, so systematic lab grading is built from that feed (see [[CRF vs Non-CRF (External) Data]]). **Local lab** values (entered in the eCRF) are often captured only when abnormal / clinically significant, and are not graded systematically — if clinically significant, the value becomes an **AE with its own investigator CTCAE grade**.

**One line:** clinical AEs are CTCAE-graded by the investigator, whatever the lab shows; the central lab is just the main source for *lab* toxicity grades, not the only place CTCAE lives.

Severity (this grade) is independent of **seriousness** (严重性) — see [[Serious Adverse Event (SAE)]] (serious ≠ severe). Different from an [[Adverse Event of Special Interest (AESI)]] (a watch based on interest, defined in advance) — AESIs are still graded with CTCAE. A grading standard used across [[Oncology]].
