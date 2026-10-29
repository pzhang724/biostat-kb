---
title: "SDTM, SDTM IG, and Conformance Rules"
type: concept
status: learned
created: 2026-06-18
---

# SDTM, SDTM IG, and Conformance Rules

Three tiers (层级) of the same CDISC tabulation (制表) standard — the **submission layer** for collected trial data (上游收集层; the analysis-ready ADaM layer is built from it, downstream).

## SDTM — Study Data Tabulation Model (研究数据制表模型)

The abstract **model / framework** (框架), not tied to any one study (study-agnostic) — the **"grammar"**. It gives a **kit of parts, not named tables** (naming the concrete domains is the IG's job), and it has **its own version numbers**, separate from the IG (Model v1.x / v2.0 vs SDTMIG v3.x). Three pillars (支柱):

**1. General observation classes (一般观测类)** — every domain is built from one of three, each with its own Topic variable:

- **Interventions** (干预) — substances/treatments **given to or taken by** the subject; Topic = the treatment (`--TRT`).
- **Events** (事件) — things that **happen to** the subject; Topic = the event term (`--TERM`).
- **Findings** (发现) — results of a **planned measurement/evaluation**; Topic = the test (`--TESTCD`). Plus a **Findings About** variant (变体).

Outside the three classes: **special-purpose** datasets (e.g. DM Demographics 人口学), **trial design**, and **relationship** datasets.

**2. Variable roles (变量角色)** — every variable has exactly one role:

- **Identifier** (标识) — `STUDYID`, `DOMAIN`, `USUBJID`, `--SEQ`.
- **Topic** (主题) — the focus of the observation.
- **Timing** (时间) — `--DTC`, `--STDTC`/`--ENDTC`, `VISITNUM`, `--DY`.
- **Qualifier** (限定) — everything else that describes the observation, split into **Grouping** (`--CAT`/`--SCAT`), **Result** (`--ORRES`/`--STRESC`/`--STRESN`), **Synonym** (`--DECOD`/`--MODIFY`), **Record** (`--SEV`, `--SER`), and **Variable** (`--ORRESU` units) qualifiers.

**3. Naming + general rules** — the **`--` two-letter domain-prefix convention** (命名约定; `--TESTCD`, `--ORRES`, `--STDTC`) makes variable names predictable across domains; core rules like **one record = one observation**, and the use of controlled terminology (受控术语).

**Model = parts + grammar (stable); the IG** names concrete domains (DM/AE/LB…) by picking a class and filling in the role variables. Model = the kit; IG = the assembled, versioned sentence.

**Who actually reads the Model?** Mostly **no one on a study team, day to day** — the **IG is the working document** (its concrete domains, variables, examples and assembly conventions answer almost every implementation question). You go back to the **Model** mainly when (1) **building a custom / non-standard domain** that the IG doesn't cover — you fall back to the three general observation classes + the role rules to build it correctly; or (2) you want the **why** behind a rule. The people who live in the Model are **CDISC standards developers / governance** (治理) (and people who build tools/validators). *Read the IG to do the work; check the Model when the IG runs out.*

## SDTM IG — Implementation Guide (实施指南)

The concrete, **versioned** specification (规范) you actually build to. It names specific **domains** (DM, AE, CM, EX, LB, VS, PC, PP, …), their variables and metadata (元数据), the expected **controlled terminology** (受控术语), and assembly conventions. "Submit SDTM datasets" = datasets built according to a given IG version. The Model is stable; the IG is what gets implemented and versioned.

### One IG for everyone — not one per therapeutic area

The SDTMIG is **single, and does not depend on the therapeutic area** (TA-agnostic) — one foundational document, versioned v3.x. It is **not** split (forked) per disease. What *is* specific to a TA is a separate CDISC product line — **Therapeutic Area User Guides (TAUGs, 治疗领域用户指南)**:

- A TAUG is a **User Guide, not an Implementation Guide** — it does **not** replace or fork the SDTMIG. It **sits on top of** SDTM + SDTMIG (+ CDASH, controlled terminology) and shows how to represent the data concepts specific to **one disease/area** — which domains to use, how to model disease-specific assessments, often adding new **test codes / variables / examples** for that area.
- CDISC has published **40+ TAUGs** (oncology, Alzheimer's, diabetes, COPD/asthma, Parkinson's, prostate cancer, virology, cardiovascular, vaccines, …).
- TAUGs are **guidance / examples**; the foundational spec you build to, which is checked for conformance, is still the **one SDTMIG**. When a TAUG adds something that is not yet in the IG, it may move into a **future IG version or a supplement**.

**One line:** one SDTMIG for everyone; what is specific to a therapeutic area lives in the separate **TAUG (user-guide) layer**, not in several IGs.

**TAUGs mapped to this wiki's TAs** ([[Oncology]] / prostate, [[Asthma]]) — checked against cdisc.org/standards/therapeutic-areas:

- **There is no single generic "Oncology" TAUG.** Oncology TAUGs are **per cancer type**: Breast Cancer, Lung Cancer, **Prostate Cancer**, Colorectal Cancer, Pancreatic Cancer. The oncology machinery shared by all of them — **tumour identification / results / response (TU / TR / RS** domains, RECIST modelling) — lives in the **SDTMIG itself**, not in a TAUG.
- **Respiratory:** **Asthma**, COPD.
- **Directly relevant here:** the **Prostate Cancer TAUG** (the prostate-cancer indication under [[Oncology]]) and the **Asthma TAUG** (the [[Asthma]] TA). Related context only: the other oncology TAUGs (Breast/Lung/Colorectal/Pancreatic) sit under the Oncology umbrella but are not this wiki's indication; **COPD** is the respiratory sibling of Asthma.

## SDTM Conformance Rules — 符合性规则

**Validation rules** (校验规则) that a machine can check, confirming that a dataset conforms to SDTM + the IG (and to controlled terminology / `define.xml`).

- Published as CDISC **Conformance Rules**; FDA also publishes its own **Validator Rules**.
- Run with tools like **Pinnacle 21** / CDISC Library.
- Results: **Errors / Warnings / Notices**; FDA rejects submissions with high-severity violations (违规).

### CDISC Conformance Rules vs FDA Validator Rules

Two layers of validation rules, split by **who issues them**:

- **CDISC Conformance Rules** — published *by CDISC* together with each standard version (SDTMIG, ADaMIG, SENDIG). The authoritative definition of what conforms to the standard, not tied to any vendor (vendor-neutral). *"Does the data follow the standard?"*
- **FDA Validator Rules** — FDA's *own* rule set (e.g. Validator Rules v1.6, Dec 2022). They include most of the CDISC Conformance Rules **plus** FDA-specific **Business Rules** (业务规则). *"Does the data follow the standard AND meet FDA's submission expectations?"* So roughly **FDA Validator Rules ⊇ CDISC Conformance Rules + FDA-specific checks**, and the FDA set is what decides FDA technical screening (技术审查).

Tools like **Pinnacle 21** run both. Reference: FDA Study Data Technical Conformance Guide, §8.

**Rules ≠ Pinnacle 21.** The rules are the **specification** (发布的规则清单 — documents/spreadsheets of what to check). **Pinnacle 21 (P21)** is the **tool/engine** (工具/引擎) that *implements* those rule sets as executable checks, runs them on your datasets, and reports Errors/Warnings/Notices (it also helps build `define.xml`). Rules = the law; P21 = the inspector. P21 is the de-facto (事实上的) validation engine for industry and FDA (FDA uses it internally), so "run P21" is short for "check conformance". But it can lag behind a rule version or have its own interpretation, so **passing P21 ≈ meeting the rules, but not exactly the same**.

**Could you build your own engine instead?** Technically yes — P21 isn't magic, just one implementation, and big sponsors/CROs (contract research organizations, 合同研究组织) do build internal validators. But the rules alone are not enough; you would still need:

1. **Rule definitions precise enough for a machine** — the published rules are a human-readable spec with ambiguity (歧义); coding each one in a fixed (deterministic) way is interpretation work (edge cases 边界情况, logic across domains/records, value-level metadata, `define.xml` conformance).
2. **The things the rules depend on** — versioned CDISC Controlled Terminology (受控术语), [[MedDRA]] and other dictionaries, the standard metadata (CDISC Library), `define.xml` — all kept in sync.
3. **Ongoing maintenance** — CDISC/FDA release new rule versions regularly; each release = re-implement + re-test. This recurring burden is the main reason people buy a P21 licence instead of building their own (DIY).
4. **Regulatory equivalence (the real catch)** — FDA runs P21 internally, so what decides your submission is FDA's verdict, not your engine's. You would still compare against P21 to predict the FDA result; a home-made engine does not free you from caring what P21/FDA says.

Bottom line: a custom engine is possible and can *add to* (complement) P21 (early/internal checks), but it does not replace it. You are not missing a secret rule — you are missing the interpretation + dependency + maintenance stack, and above all regulatory equivalence with FDA's tool.

Addresses:
- FDA Validator Rules + Business Rules → FDA Study Data Standards Resources: <https://www.fda.gov/industry/fda-data-standards-advisory-board/study-data-standards-resources>
- CDISC Conformance Rules → <https://www.cdisc.org/standards/conformance-rules>

### Business Rules vs Validator Rules

The same intent, at two levels:

- **FDA Business Rules** (业务规则) — high-level statements of **what** FDA expects of study data and **why** (policy/requirement level). Conceptual, written for humans, with **no severity** assigned. *"Data must support meaningful review."*
- **FDA Validator Rules** (校验规则) — the concrete, **machine-executable implementation** of those Business Rules: the specific checks a validator runs. Published by FDA for transparency (透明); in effect, the subset of Pinnacle 21 validator rules that implement the Business Rules.

So **Business Rules = the "what/why" (policy); Validator Rules = the "how" (executable checks that enforce it)**. Severity (严重度): neither the CDISC Conformance Rules nor the FDA Business Rules have a severity, and FDA Validator Rules don't publish one either — P21 adds its own Type = Error / Warning / Notice.

### Does FDA officially endorse P21?

There is no formal (de-jure, 法律上的) endorsement and **no requirement** that sponsors use P21 — FDA guidance (the Technical Conformance Guide) is written without naming a tool (tool-agnostic). **But** FDA has licensed and used **Pinnacle 21 Enterprise internally** to screen incoming submissions for more than ten years. Because FDA's own screening runs P21, it is the **de-facto standard** — sponsors run the same tool to predict the FDA result. (De-facto through FDA's own use, not a "you must use this product" rule.)

### Do the three rule sets cover "all the rules"?

Mostly right in intent, with two corrections:

1. **They overlap / nest (嵌套) — they don't add up as separate (disjoint) sets.** CDISC Conformance Rules = conformance to the CDISC standards; FDA Validator Rules already **include** most of those CDISC checks **plus** FDA-specific ones (and they are the executable form of the FDA Business Rules). So together they ≈ "basically all the **automated** checks that matter for a submission", but through heavy overlap, not A + B + C.
2. **Automated rules ≠ everything you must do.** Many requirements live in the standards/IG and guidance and are **not** coded as any machine rule — traceability (可追溯性), data fitness (数据适用性), reviewer judgment. Automated rules are a **floor** (底线), not the whole obligation. Other agencies also have their own sets (**PMDA Validation Rules** for Japan, NMPA for China).

"Interpretation differences cause deviation" is exactly right: the same rule text, implemented differently (P21 vs a home-made engine vs FDA's internal run), handles edge cases differently, and versions lag behind.

**Other documents to reference** (the source-of-truth / governing layer that the rules *come from*):

- The **IGs** themselves — [SDTM/SDTMIG](https://www.cdisc.org/standards/foundational/sdtm) · [ADaM/ADaMIG](https://www.cdisc.org/standards/foundational/adam) · [SENDIG](https://www.cdisc.org/standards/foundational/send) · [Define-XML](https://www.cdisc.org/standards/data-exchange/define-xml).
- **FDA Study Data Technical Conformance Guide** — the governing FDA document that ties it together: <https://www.fda.gov/regulatory-information/search-fda-guidance-documents/study-data-technical-conformance-guide-technical-specifications-document>
- **FDA Data Standards Catalog** — which standard versions FDA supports/requires (on the [FDA Study Data Standards Resources](https://www.fda.gov/industry/fda-data-standards-advisory-board/study-data-standards-resources) page).
- **CDISC Controlled Terminology** — the codelists the rules check against: <https://www.cdisc.org/standards/terminology/controlled-terminology>
- Reviewer's guides — **cSDRG** (clinical Study Data Reviewer's Guide, for SDTM) / **ADRG** (Analysis Data Reviewer's Guide, for ADaM), PHUSE templates: <https://phuse.global/Deliverables>
- **PMDA Validation Rules** (Japan): <https://www.pmda.go.jp/english/review-services/reviews/0002.html>; other regions are similar.

## What's in an SDTM (mapping) spec

The **mapping specification** (映射规范) of a study, often an Excel workbook, is more than variable→variable — it is basically the **human-readable source** from which `define.xml` is generated. CT / codelists **are** part of it, not optional. Typical parts:

1. **Datasets / Domains metadata** — for each domain: name, label, class (Interventions / Events / Findings / Special-Purpose), structure (*one record per…*), key variables.
2. **Variable-level mapping** (for each domain) — the core tab. Exact columns:

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
   | Origin | CRF / Derived / Assigned / Protocol / eDT (electronic data transfer) |
   | Source dataset + variable | the raw/EDC field |
   | Mapping / Derivation logic | the algorithm/rule in words |
   | Comments | |
3. **Codelists / Controlled Terminology** tab — each codelist: name + NCI/CDISC code, submission value (提交值), decode (解码). It covers both CDISC CT (受控术语; see [[MedDRA]] for dictionaries) and codelists specific to the study/sponsor. **CT vs codelist** are not opposites: **CT (CDISC Controlled Terminology) = the standard library** (maintained by NCI-EVS — National Cancer Institute Enterprise Vocabulary Services; versioned; every list has an NCI **C-code**); a **codelist = the unit** (one named set of allowed values). The split between standard and self-defined is *within* codelists — a codelist is either a **CDISC-standard** one (it has a C-code, e.g. SEX/RACE/AESEV/`--TESTCD`), a **self-defined** one from the sponsor/study (you write it), or a **standard-but-extended** one (CDISC marks each codelist **Extensible Yes/No** — extensible (可扩展) ⇒ you may add sponsor terms; non-extensible ⇒ CDISC values only). In `define.xml` each codelist is tagged to match. **Where CDISC CT lives:** developed by CDISC but published/hosted by **NCI-EVS** (a new version about every quarter) — overview at <https://www.cdisc.org/standards/terminology/controlled-terminology>; the actual files to download (per standard: SDTM/ADaM/CDASH/SEND/Define-XML) on the NCI-EVS FTP <https://evs.nci.nih.gov/ftp1/CDISC/>; single terms/C-codes can be searched in the NCI Term Browser <https://nciterms.nci.nih.gov>; access by program through the CDISC Library API <https://www.cdisc.org/cdisc-library>. **It really is an Excel** — one `.xls` per standard (not one combined file), which is why cdisc.org does not link to a single file. Direct: SDTM CT Excel `https://evs.nci.nih.gov/ftp1/CDISC/SDTM/SDTM Terminology.xls` (the same folder has a `…Changes.xls` diff + `Archive/`); swap the folder for ADaM/CDASH/SEND. One Excel = all of that standard's codelists, with NCI C-codes, submission values, decodes, and Extensible Yes/No.
4. **Value-Level Metadata (VLM, 值级元数据)** — for Findings domains keyed by `--TESTCD` (LB, VS, PC, QS…): the type/units/CT/derivation for each test, which vary from row to row.
5. **Computational methods / derivations** (计算方法/衍生) — named algorithms that the mapping refers to.
6. **External dictionaries** — the MedDRA and WHODrug versions used for coding.
7. **SUPPQUAL** (`SUPP--`) and **RELREC** relationship mapping.
8. Comments / document & study metadata.

So the "exact mapping" = the set of columns in #2 (target variable + metadata + origin + source + logic + codelist); the CT/codelists in #3–4 are a **required companion**. Spec ≈ `define.xml` in human-readable form.

### Spec ↔ define.xml

The same **metadata backbone**, on different sides of the build:

- **SDTM spec** = the **blueprint written by humans** (Excel) that programmers build *to* — the **"how to build it"**. Besides dataset/variable metadata, it has the **source dataset + variable** and the **derivation/mapping logic in words** (instructions for raw/EDC → SDTM).
- **`define.xml`** = the **machine-readable metadata deliverable** (交付物) (the CDISC **Define-XML** standard, v2.0/2.1), submitted to FDA *together with* the datasets — the **"data guide"** that describes the **final datasets** ("what the data is", not how it was built).

**Direction:** the spec is the **source**; `define.xml` is **generated from it** (and must match the actual datasets) — hence "spec ≈ define.xml in human-readable form".

**Shared:** datasets/domains, variables (type/length/role/core), codelists/CT, [[#What's in an SDTM (mapping) spec|VLM]], computational methods/derivations, origins, comments.

**Differences:**

- **Audience/format** — spec = internal, Excel, for humans; `define.xml` = external/regulatory, XML, machine-readable.
- The spec keeps the **source→target mapping + the full programming logic**; `define.xml` **leaves out the path of the raw source field** (it records the **Origin**, and computational methods for derivations, but not "which EDC variable").
- **Timing** — the spec is written *first*, to build the data; `define.xml` is produced *at the end*, to describe what was built.
- `define.xml` is itself a **standard submission artifact that is checked for conformance** (P21 validates it); the spec format is defined by the sponsor and is not submitted.

**One line:** spec = the build instructions (with source + logic); `define.xml` = the standard, submittable description of the finished datasets, generated from that spec.

#### XML vs YAML format — which is "better"?

It's not either/or; they win at different layers, and for the deliverable you **don't get to choose**:

- **As the submission deliverable → XML wins (no choice).** FDA/PMDA (Japan's regulator) **require CDISC Define-XML** — it is what regulators accept and what P21 validates. XML's advantage here: an official **schema** (模式) to validate against, **namespaces/extensibility** (命名空间/可扩展性), mature tools, and it **turns into human-readable HTML through an XSL stylesheet** (样式表). The cost: it is wordy (verbose) and painful to write by hand.
- **As a human authoring/source format → YAML is nicer.** Short, readable, **friendly to git diffs**, easy to edit by hand. But it has **no regulatory standing**, **no official define schema**, weaker validation, no built-in rendering, and its sensitivity to whitespace (空格敏感) becomes error-prone at scale.

So the practical pattern is **both**: write in a friendly source (YAML or the Excel spec) → **generate the required `define.xml`**. (Aside: CDISC is moving the *data* format toward **Dataset-JSON**, but **Define stays XML** — there is no YAML define standard.)

**One line:** for submission, `define.xml` is required and wins; YAML only beats it as a human-editable source that you compile down to `define.xml`.

## Visit numbering: VISITNUM (SDTM) vs AVISITN (ADaM)

How [[Schedule of Assessments#Why there are unscheduled visits|unscheduled visits]] get numbered:

- **How the SDTM IG frames it:** **planned** visits live in the **`TV` (Trial Visits)** domain — TV holds *scheduled visits only*. The IG rule: `VISIT`+`VISITNUM` in subject-level domains must **match TV, *except* for unscheduled / unplanned visits** (the IG makes this exception explicitly). So unscheduled visits simply don't appear in TV; they are recorded in **`SV`** (subject visits) and in the data domains, with numbers assigned by the sponsor.
- **`VISITNUM` (SDTM)** is a **numeric sort key** (排序键) for time order — not a date. The IG gives a *convention* but not a required scheme (sponsor-defined, documented in `define.xml` / cSDRG). The convention:
  - **Insert a decimal** between the scheduled visits on either side, keeping time order — two unscheduled visits between visit 3 and 4 → **3.1, 3.2**.
  - **Same date as a planned visit** → the planned `VISITNUM` **+ 0.01**.
  - `VISIT` for unplanned visits is often **left null** (or "UNSCHEDULED"), as the sponsor chooses; `VISITDY`/`SVSTDTC` carry the actual timing.
  - *Tension (矛盾):* validators (Pinnacle 21 checks, e.g. **SD1023 / SD1060**) police visit consistency. The `VISIT`↔`VISITNUM` match is checked *against TV, with the unscheduled exception*, so the unscheduled scheme must be done the expected way, or justified in the cSDRG.
- **`AVISITN` (ADaM)** is a **different, derived** thing: ADaM BDS (basic data structure) has its own pair of analysis-visit variables, **`AVISIT` (char) + `AVISITN` (numeric sort)**, derived by **visit windowing** (访视窗口化) per the SAP — independent of `VISITNUM`, and it does not have to equal it (e.g. Baseline=0, Week 4=4, Week 8=8). Unscheduled SDTM records are either **windowed into the nearest nominal analysis visit** (feeding by-visit tables, with "closest to target" / "worst case" rules picking the winning record), or flagged **`AVISIT="Unscheduled"`** / excluded if the SAP only summarizes scheduled timepoints.

**Mental model:** `VISITNUM` = the collection/sort order of what *actually happened* (SDTM keeps the raw truth, including unscheduled visits); `AVISITN` = the analysis order *after windowing* (ADaM decides how unscheduled visits fold into the planned grid).

**Whose decision — and where it is written:** whether an unscheduled record can count toward a given `AVISIT` is an **analysis** decision. It is defined in the **SAP** (statistical analysis plan, 统计分析计划) and put into practice in the ADaM spec / `define.xml` — **not** in SDTM or the IG. The **protocol** specifies the *operational* visit windows of the SoA (acceptable timing for running the trial); the **SAP** specifies the *analysis* visit-windowing algorithm — which actual/unscheduled assessments map to which analysis visit, and the tie-break rule (平局规则) when several fall in one window (e.g. closest to the nominal day, or last/worst). **If the protocol says nothing (the usual case), the SAP must define it** — it is the statistician's responsibility, and it has to be explicit, or the derivation cannot be reproduced. Protocol = conduct windows; SAP = analysis windows + handling of unscheduled visits.

## Events vs Findings timing — how an AE's occurrence is timed

A scheduled lab and an AE are timed in completely different ways, because they are in different SDTM **observation classes**:

- A scheduled lab (`LB`) is a **Finding** — taken at a planned timepoint, tagged with `VISIT`/`VISITNUM` + the collection date (`--DTC`). Its timing **is** the [[Schedule of Assessments]] grid.
- An AE (`AE`) is an **Event** — it is **driven by the event, not by the visit**. It carries its **own onset date/time `AESTDTC`** (and end `AEENDTC`) — the actual calendar date when the event started, independent of any visit. There is no fixed timepoint slot for it.

**Ascertainment (how it is found) vs timing (what is recorded)** are separate:

- AEs are collected **continuously** across the whole [[Serious Adverse Event (SAE)#Safety reporting period|safety reporting period]] — reported by the patient (between or at visits), observed by the investigator, or **triggered by a scheduled assessment** (a scheduled lab comes back abnormal → it can become an AE). So scheduled labs *feed* AE detection. How AEs are found (solicited vs spontaneous, many sources) is [[Adverse Event Ascertainment]].
- At every visit the investigator **asks about** AEs (solicits: "anything new since the last visit?"); events off the schedule come in through [[Schedule of Assessments#Why there are unscheduled visits|unscheduled visits]] / phone calls.
- But however it is found, the **recorded time is the AE's own onset date `AESTDTC`**, not the visit when it was captured. **Partial/unknown dates** (不完整日期) are allowed when the exact onset is not known.

## Relationship

> Model (abstract framework) → **IG** (the concrete versioned spec you implement) → **Conformance Rules** (automated checks that the implementation is valid).

Chapter-by-chapter read-through: [[SDTMIG Fundamentals (Chapter 2)]].

Related: [[MedDRA]] is the controlled terminology used to code AE/medical-history domains; [[Pharmacokinetics (PK)]] data goes into the **PC/PP** domains here. A data standard used across [[Oncology]].
