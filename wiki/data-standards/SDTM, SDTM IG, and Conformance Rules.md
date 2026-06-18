---
title: "SDTM, SDTM IG, and Conformance Rules"
type: concept
status: learned
tags: [standards, regulatory, data-management]
created: 2026-06-18
updated: 2026-06-18
sources: 1
---

# SDTM, SDTM IG, and Conformance Rules

Three tiers of the same CDISC tabulation (制表) standard — the **submission layer** for collected trial data (上游收集层；the analysis-ready ADaM layer is built downstream from it).

## SDTM — Study Data Tabulation Model (研究数据制表模型)

The abstract **model / framework** (框架), not a list of tables. Defines:

- Data organized as **observations** in **domains** (域 — one table per topic).
- **Classes** (类别): Interventions (干预)、Events (事件)、Findings (发现), plus special-purpose (e.g. DM Demographics).
- Standard **variable roles** (变量角色): Identifier (标识)、Topic (主题)、Timing (时间)、Qualifier (限定).
- Rules like one record = one observation.

It is the "grammar," stable across studies.

## SDTM IG — Implementation Guide (实施指南)

The concrete, **versioned** spec you actually build to. Names specific **domains** (DM, AE, CM, EX, LB, VS, PC, PP, …), their variables and metadata, expected **controlled terminology** (受控术语), and assembly conventions. "Submit SDTM datasets" = datasets built per a given IG version. Model is stable; the IG is what gets implemented and versioned.

## SDTM Conformance Rules — 符合性规则

Machine-checkable **validation rules** (校验规则) confirming a dataset conforms to SDTM + the IG (and to controlled terminology / `define.xml`).

- Published as CDISC **Conformance Rules**; FDA also publishes its own **Validator Rules**.
- Run via tools like **Pinnacle 21** / CDISC Library.
- Results: **Errors / Warnings / Notices**; FDA rejects submissions with high-severity violations.

## Relationship

> Model (abstract framework) → **IG** (concrete versioned spec you implement) → **Conformance Rules** (automated checks that the implementation is valid).

Related: [[MedDRA]] is the controlled terminology used to code AE/medical-history domains; [[Pharmacokinetics (PK)]] data lands in the **PC/PP** domains here. A cross-cutting data standard in [[Oncology]].
