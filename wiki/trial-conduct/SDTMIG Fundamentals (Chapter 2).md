---
title: "SDTMIG Fundamentals (Chapter 2)"
type: concept
status: learning
created: 2026-06-19
---

# SDTMIG Fundamentals (Chapter 2)

A read-through of **SDTMIG v3.4 §2** (SDTM Implementation Guide, SDTM 实施指南) — the IG's practical restatement of the [[SDTM, SDTM IG, and Conformance Rules#SDTM — Study Data Tabulation Model (研究数据制表模型)|SDTM Model]]. What is **new compared with the Model page** is marked below.

## 2.1 Observations & variables — **5 roles** (not 4)

The IG lists **five** main variable roles (变量角色) — the Model page had only four; the fifth is **Rule**:

- **Identifier** (标识) · **Topic** (主题) · **Timing** (时间) · **Qualifier** (限定) — as before.
- **Rule variables** (规则) — **new**: they express the condition to **start / end / branch (分支) / loop (循环)** in the **Trial Design Model** (试验设计模型; e.g. `TABRANCH`, `TATRANS`, element `TESTRL`/`TEENRL`). Only in trial-design datasets.

Qualifier still has its **5 subclasses** (子类): Grouping (`--CAT/--SCAT`), Result (`--ORRES/--STRESC/--STRESN`), Synonym (同义; `--MODIFY/--DECOD`, `--TEST/--LOINC`, LOINC = Logical Observation Identifiers Names and Codes), Record (attributes of the whole record — SAE flags, AGE/SEX/RACE, `--BLFL/--SPEC/--LOC`), Variable (modifies one variable — `--ORRESU/--ORNRHI/--ORNRLO` qualify `--ORRES`; `--DOSU` qualifies `--DOSE`).

## 2.2 Datasets & domains — **DOMAIN code used 4 ways**

A domain = logically related observations with a **common topic**, in one dataset, with one **2-character code**. That code is used in **4 ways**: (1) the dataset name, (2) the value of the `DOMAIN` variable, (3) the **prefix** (前缀) on most variable names, (4) the value of `RDOMAIN` in relationship tables. All datasets are **flat files** (扁平文件; rows = observations, columns = variables); the metadata (元数据) travels in **Define-XML** ([[SDTM, SDTM IG, and Conformance Rules#Spec ↔ define.xml|define.xml]]).

## 2.3 The 3 general observation classes (干预/事件/发现)

- **Interventions** — treatments **given to the subject or taken by the subject themselves** (self-administered) that have a physiological (生理) effect (study drug EX, con-meds CM, alcohol/tobacco SU substance use).
- **Events** — planned **milestones** (里程碑; randomization, completion) **plus** things that happen independently of planned evaluations (AE, MH).
- **Findings** — results of **planned evaluations** (LB, EG, QS). **Most data ends up here** (measurements / answers to questions).

## 2.4 The 4 non-GOC dataset types

Not everything fits the 3 general observation classes (GOC):

1. **Special-purpose** (特殊用途) — subject data outside the classes: **DM, CO, SE, SV** (demographics, comments, subject elements, subject visits) (§5).
2. **Trial Design Model (TDM)** — the study design, **no subject data**: TA, TE (trial arms, trial elements)… (§7).
3. **Relationship** (关系) — **RELREC, SUPP--** (§8).
4. **Study Reference** (研究参考) — Device Identifiers **DI**, Non-host Organism Identifiers **OI** (§9).

## 2.5 Standard domain models — Core & Permissible rules

- Submit **only the domains actually collected** (or derived directly). Which data to collect is decided by the science, not by SDTM. Anything in an [[SDTM, SDTM IG, and Conformance Rules|ADaM]] dataset must be **traceable** (可追溯) back to SDTM.
- **STUDYID, USUBJID, DOMAIN, `--SEQ`** are required in every GOC domain. Any Timing variable and any Qualifier of the same class may be added, unless a domain restricts it.
- You **cannot** add variables outside that (non-SDTM variables go to **SUPPQUAL**, supplemental qualifiers 补充限定); you **cannot rename or change** standard variables or their metadata.
- **Permissible variable rule** (允许变量规则): if the study **collected** that item → the variable **must** be included (even if it is null); if it **didn't** → the variable **must not** appear (and must not be declared in define.xml).

## 2.6 Creating a new (custom) domain

Only when no published domain fits, and it **must** be built on one of the 3 classes. Key rules:

- Group by **common topic / nature of the data**, not by **how it was collected**; subdivide with `--CAT/--SCAT/--METHOD/--SPEC/--LOC`.
- **Don't split by time** — prior + current go in one domain (CM). **Exception: AE & MH** (for regulatory reporting).
- **Don't** create a domain based on **how the data is used**: BP (blood pressure) endpoints still go in **VS**, liver function tests (LFTs, 肝功能检查) of special interest still go in **LB** — no custom "efficacy" domain.
- Data in a parent→child hierarchy (父子层级) → a **domain pair** (MB/MS microbiology specimen/susceptibility, PC/PP), grouped through `DOMAIN` so that RELREC can link them at dataset level.
- Build steps: the required Identifiers → the class's **Topic** variable → **Qualifiers** of the same class (no variables from other classes) → **Timing** variables → pick a **2-character code** (not already in CDISC CT, controlled terminology; **`AD/AX/AP/SQ/SA` are forbidden**) → apply the prefix → standard order → labels in title case (首字母大写) → describe it in Define-XML → non-standard variables to SUPPQUAL.

## 2.7 Variables not allowed

A set of **SEND (Standard for Exchange of Nonclinical Data, 非临床数据交换标准) variables must never** appear in SDTM for human trials — e.g. `--METHOD` (Interventions), `--USCHFL`, the `RP*`/`--NOM*` reproductive-timing (生殖时间) variables; and `SPECIES/STRAIN/SBSTRAIN` never in **DM** (all subjects are human). A few (`--ANTREG/--CHRON/--DISTR`, `SETCD`) have not been evaluated yet → use them only with great caution; `POOLID` is allowed when needed.

Part of the [[SDTM, SDTM IG, and Conformance Rules]] read-through; used across [[Oncology]].
