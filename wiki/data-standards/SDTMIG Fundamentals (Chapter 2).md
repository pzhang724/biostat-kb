---
title: "SDTMIG Fundamentals (Chapter 2)"
type: concept
status: learning
tags: [standards, data-management]
created: 2026-06-19
updated: 2026-06-19
sources: 1
---

# SDTMIG Fundamentals (Chapter 2)

Read-through of **SDTMIG v3.4 §2** — the IG's practical restatement of the [[SDTM, SDTM IG, and Conformance Rules#SDTM — Study Data Tabulation Model (研究数据制表模型)|SDTM Model]]. What's **new vs the Model page** is flagged below.

## 2.1 Observations & variables — **5 roles** (not 4)

The IG lists **five** major variable roles — the Model page only had four; the fifth is **Rule**:

- **Identifier** (标识) · **Topic** (主题) · **Timing** (时间) · **Qualifier** (限定) — as before.
- **Rule variables** (规则) — **new**: express the condition to **start / end / branch / loop** in the **Trial Design Model** (e.g. `TABRANCH`, `TATRANS`, element `TESTRL`/`TEENRL`). Only in trial-design datasets.

Qualifier still has its **5 subclasses**: Grouping (`--CAT/--SCAT`), Result (`--ORRES/--STRESC/--STRESN`), Synonym (`--MODIFY/--DECOD`, `--TEST/--LOINC`), Record (whole-record attrs — SAE flags, AGE/SEX/RACE, `--BLFL/--SPEC/--LOC`), Variable (modifies one var — `--ORRESU/--ORNRHI/--ORNRLO` qualify `--ORRES`; `--DOSU` qualifies `--DOSE`).

## 2.2 Datasets & domains — **DOMAIN code used 4 ways**

A domain = logically related observations with a **common topic**, one dataset, one **2-char code**. That code is used **4 ways**: (1) dataset name, (2) value of the `DOMAIN` variable, (3) **prefix** on most variable names, (4) value of `RDOMAIN` in relationship tables. All datasets are **flat files** (rows=obs, cols=vars); metadata travels in **Define-XML** ([[SDTM, SDTM IG, and Conformance Rules#Spec ↔ define.xml|define.xml]]).

## 2.3 The 3 general observation classes (干预/事件/发现)

- **Interventions** — treatments **given to / self-administered by** the subject with a physiological effect (study drug EX, con-meds CM, alcohol/tobacco SU).
- **Events** — planned **milestones** (randomization, completion) **plus** occurrences independent of planned evaluations (AE, MH).
- **Findings** — results of **planned evaluations** (LB, EG, QS). **Most data lands here** (measurements / answers to questions).

## 2.4 The 4 non-GOC dataset types

Not everything fits the 3 classes:

1. **Special-purpose** — subject data outside the classes: **DM, CO, SE, SV** (§5).
2. **Trial Design Model (TDM)** — study design, **no subject data**: TA, TE… (§7).
3. **Relationship** — **RELREC, SUPP--** (§8).
4. **Study Reference** — Device Identifiers **DI**, Non-host Organism Identifiers **OI** (§9).

## 2.5 Standard domain models — Core & Permissible rules

- Submit **only domains actually collected** (or directly derived). Data choice is driven by science, not SDTM. Anything in an [[SDTM, SDTM IG, and Conformance Rules|ADaM]] dataset must be **traceable** back to SDTM.
- **STUDYID, USUBJID, DOMAIN, `--SEQ`** required in every GOC domain. Any Timing var and any same-class Qualifier may be added unless a domain restricts it.
- **Cannot** add variables outside that (non-SDTM vars go to **SUPPQUAL**); **cannot rename/modify** standard variables or their metadata.
- **Permissible variable rule**: if the study **collected** that item → the var **must** be included (even if null); if it **didn't** → the var **must not** appear (nor be declared in define.xml).

## 2.6 Creating a new (custom) domain

Only when no published domain fits, and it **must** be built on one of the 3 classes. Key rules:

- Group by **common topic / nature of data**, not by **collection method**; subdivide with `--CAT/--SCAT/--METHOD/--SPEC/--LOC`.
- **Don't split by time** — prior + current in one domain (CM). **Exception: AE & MH** (regulatory reporting).
- **Don't** create a domain by **how data is used**: BP endpoints still go in **VS**, special-interest LFTs still in **LB** — no custom "efficacy" domain.
- Hierarchical parent→child data → a **domain pair** (MB/MS, PC/PP), grouped via `DOMAIN` so RELREC can link them at dataset level.
- Build steps: required Identifiers → class **Topic** var → same-class **Qualifiers** (no cross-class vars) → **Timing** vars → pick a **2-char code** (not already CDISC CT; **`AD/AX/AP/SQ/SA` forbidden**) → apply prefix → standard order → title-case labels → describe in Define-XML → non-standard vars to SUPPQUAL.

## 2.7 Variables not allowed

A set of **SEND (nonclinical) variables must never** appear in human-trial SDTM — e.g. `--METHOD` (Interventions), `--USCHFL`, the `RP*`/`--NOM*` repro-timing vars; and `SPECIES/STRAIN/SBSTRAIN` never in **DM** (all subjects are human). A few (`--ANTREG/--CHRON/--DISTR`, `SETCD`) are unevaluated → use with extreme caution; `POOLID` is allowed when needed.

Part of the [[SDTM, SDTM IG, and Conformance Rules]] read-through; cross-cutting in [[Oncology]].
