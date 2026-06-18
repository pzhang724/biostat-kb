---
title: "SDTM, SDTM IG, and Conformance Rules"
type: concept
status: learned
tags: [standards, regulatory, data-management]
created: 2026-06-18
updated: 2026-06-18
sources: 7
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

### CDISC Conformance Rules vs FDA Validator Rules

Two layers of validation rules, split by **who issues them**:

- **CDISC Conformance Rules** — published *by CDISC* alongside each standard version (SDTMIG, ADaMIG, SENDIG). The authoritative, vendor-neutral definition of what conforms to the standard. *"Does the data follow the standard."*
- **FDA Validator Rules** — FDA's *own* rule set (e.g. Validator Rules v1.6, Dec 2022). Largely incorporate the CDISC Conformance Rules **plus** FDA-specific **Business Rules** (业务规则). *"Does the data follow the standard AND meet FDA submission expectations."* So roughly **FDA Validator Rules ⊇ CDISC Conformance Rules + FDA-specific checks**, and the FDA set is what gates FDA technical screening.

Tools like **Pinnacle 21** run both. Reference: FDA Study Data Technical Conformance Guide, §8.

**Rules ≠ Pinnacle 21.** The rules are the **specification** (发布的规则清单 — documents/spreadsheets of what to check). **Pinnacle 21 (P21)** is the **tool/engine** (工具/引擎) that *implements* those rule sets as executable checks, runs them against your datasets, and reports Errors/Warnings/Notices (also helps build `define.xml`). Rules = the law; P21 = the inspector. P21 is the de-facto industry + FDA validation engine (FDA uses it internally), so "run P21" is shorthand for "check conformance" — but it can lag a rule version or carry its own interpretation, so **passing P21 ≈ meeting the rules, not identical to it**.

**Could you build your own engine instead?** Technically yes — P21 isn't magic, just one implementation, and big sponsors/CROs do build internal validators. But the rules alone aren't enough; you'd still need:

1. **Machine-precise rule definitions** — published rules are human-readable spec with ambiguity; coding each deterministically is interpretation work (edge cases, cross-domain/cross-record logic, value-level metadata, `define.xml` conformance).
2. **Dependencies the rules reference** — versioned CDISC Controlled Terminology (受控术语), [[MedDRA]] and other dictionaries, the standard metadata (CDISC Library), `define.xml` — kept in sync.
3. **Ongoing maintenance** — CDISC/FDA reissue rule versions regularly; each release = re-implement + re-test. This recurring burden is the main reason people license P21 over DIY.
4. **Regulatory equivalence (the real catch)** — FDA runs P21 internally, so what gates your submission is FDA's verdict, not your engine's. You'd still benchmark against P21 to predict the FDA result; a home-grown engine doesn't free you from caring what P21/FDA says.

Bottom line: a custom engine is feasible and can *complement* P21 (early/internal checks), but doesn't replace it. You're not missing a secret rule — you're missing the interpretation + dependency + maintenance stack, and above all regulatory equivalence to FDA's tool.

Addresses:
- FDA Validator Rules + Business Rules → FDA Study Data Standards Resources: <https://www.fda.gov/industry/fda-data-standards-advisory-board/study-data-standards-resources>
- CDISC Conformance Rules → <https://www.cdisc.org/standards/conformance-rules>

### Business Rules vs Validator Rules

Same intent, two altitudes:

- **FDA Business Rules** (业务规则) — high-level statements of **what** FDA expects of study data and **why** (policy/requirement level). Conceptual, human-oriented, **no severity** assigned. *"Data must support meaningful review."*
- **FDA Validator Rules** (校验规则) — the concrete, **machine-executable implementation** of those Business Rules: the specific checks a validator runs. Published by FDA for transparency; effectively the subset of Pinnacle 21 validator rules that implement the Business Rules.

So **Business Rules = the "what/why" (policy); Validator Rules = the "how" (executable checks that enforce it)**. Severity (严重度): neither CDISC Conformance Rules nor FDA Business Rules carry severity, and FDA Validator Rules don't publish it either — P21 adds its own Type = Error / Warning / Notice.

### Does FDA officially endorse P21?

No *de-jure* endorsement and **no mandate** that sponsors use P21 — FDA guidance (Technical Conformance Guide) is written tool-agnostically. **But** FDA has licensed and used **Pinnacle 21 Enterprise internally** to screen incoming submissions for over a decade. Because FDA's own screening runs P21, it is the **de-facto standard** — sponsors run the same tool to predict the FDA result. (De-facto via FDA's own usage, not a "you must use this product" rule.)

### Do the three rule sets cover "all the rules"?

Mostly right in intent, with two corrections:

1. **They overlap / nest — they don't add up as disjoint sets.** CDISC Conformance Rules = conformance to the CDISC standards; FDA Validator Rules already **incorporate** most of those CDISC checks **plus** FDA-specific ones (and are the executable form of the FDA Business Rules). So the union ≈ "essentially all the **automated** checks that matter for a submission," but via heavy overlap, not A + B + C.
2. **Automated rules ≠ everything you must do.** Many requirements live in the standards/IG and guidance and are **not** encoded as any machine rule — traceability, data fitness, reviewer judgment. Automated rules are a **floor**, not the whole obligation. Other agencies also have their own sets (**PMDA Validation Rules** for Japan, NMPA for China).

"Interpretation differences cause deviation" is exactly right: same rule text, different implementations (P21 vs a home engine vs FDA's internal run) interpret edge cases differently, and versions lag.

**Other documents to reference** (the source-of-truth / governing layer rules *derive* from):

- The **IGs** themselves — [SDTM/SDTMIG](https://www.cdisc.org/standards/foundational/sdtm) · [ADaM/ADaMIG](https://www.cdisc.org/standards/foundational/adam) · [SENDIG](https://www.cdisc.org/standards/foundational/send) · [Define-XML](https://www.cdisc.org/standards/data-exchange/define-xml).
- **FDA Study Data Technical Conformance Guide** — the governing FDA document tying it together: <https://www.fda.gov/regulatory-information/search-fda-guidance-documents/study-data-technical-conformance-guide-technical-specifications-document>
- **FDA Data Standards Catalog** — which standard versions FDA supports/requires (on the [FDA Study Data Standards Resources](https://www.fda.gov/industry/fda-data-standards-advisory-board/study-data-standards-resources) page).
- **CDISC Controlled Terminology** — the codelists the rules check against: <https://www.cdisc.org/standards/terminology/controlled-terminology>
- Reviewer's guides — **cSDRG** (clinical SDTM) / **ADRG** (ADaM), PHUSE templates: <https://phuse.global/Deliverables>
- **PMDA Validation Rules** (Japan): <https://www.pmda.go.jp/english/review-services/reviews/0002.html>; other regions analogous.

## What's in an SDTM (mapping) spec

The study-level **mapping specification** (映射规范, often an Excel workbook) is more than variable→variable — it is essentially the **human-readable source** that `define.xml` is generated from. CT / codelists **are** part of it, not optional. Typical components:

1. **Datasets / Domains metadata** — per domain: name, label, class (Interventions / Events / Findings / Special-Purpose), structure (*one record per…*), key variables.
2. **Variable-level mapping** (per domain) — the core tab. Exact columns:

   | Column | Meaning |
   |---|---|
   | Domain | e.g. AE |
   | Variable Name | target SDTM variable (e.g. `AESTDTC`) |
   | Variable Label | |
   | Type | Char / Num |
   | Length | |
   | Role | Identifier / Topic / Timing / Qualifier |
   | Core | Req / Exp / Perm |
   | Codelist / CT | which codelist the value must come from |
   | Origin | CRF / Derived / Assigned / Protocol / eDT |
   | Source dataset + variable | the raw/EDC field |
   | Mapping / Derivation logic | the algorithm/rule in words |
   | Comments | |
3. **Codelists / Controlled Terminology** tab — each codelist: name + NCI/CDISC code, submission value, decode. Covers both CDISC CT (受控术语, see [[MedDRA]] for dictionaries) and study-/sponsor-specific codelists.
4. **Value-Level Metadata (VLM)** — for Findings domains keyed by `--TESTCD` (LB, VS, PC, QS…): per-test type/units/CT/derivation that vary row to row.
5. **Computational methods / derivations** — named algorithms referenced by the mapping.
6. **External dictionaries** — MedDRA, WHODrug versions used for coding.
7. **SUPPQUAL** (`SUPP--`) and **RELREC** relationship mapping.
8. Comments / document & study metadata.

So the "exact mapping" = the column set in #2 (target var + metadata + origin + source + logic + codelist); the CT/codelists in #3–4 are a **required companion**. Spec ≈ `define.xml` in human-readable form.

## Relationship

> Model (abstract framework) → **IG** (concrete versioned spec you implement) → **Conformance Rules** (automated checks that the implementation is valid).

Related: [[MedDRA]] is the controlled terminology used to code AE/medical-history domains; [[Pharmacokinetics (PK)]] data lands in the **PC/PP** domains here. A cross-cutting data standard in [[Oncology]].
