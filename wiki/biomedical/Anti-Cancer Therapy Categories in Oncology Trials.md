---
title: "Anti-Cancer Therapy Categories in Oncology Trials"
type: concept
status: learned
tags: [trial-conduct, data-management]
created: 2026-06-11
updated: 2026-06-19
sources: 3
---

# Anti-Cancer Therapy Categories in Oncology Trials

In an oncology trial, cancer-directed treatments are sorted into non-overlapping buckets by their **role relative to the study drug**. The study drug is the studied "independent variable"; every other anti-cancer therapy is a confounder to control or explain.

Pharmacologically, the study drug *is* a type of anti-cancer therapy — the buckets below are a **trial-data distinction**, not a biological one.

- **Study drug / Investigational Product (IP)** — the single product being evaluated for safety/efficacy. SDTM **EX** (EC if needed).
- **Prior anti-cancer therapy** — treatments before enrollment. Drives eligibility, washout, line of therapy, refractory status. SDTM **CM** (drugs) / **PR** (radiation, surgery).
- **Concomitant anti-cancer therapy** — usually *prohibited* during study; if it occurs it contaminates efficacy/safety attribution (often a protocol deviation).
- **Subsequent anti-cancer therapy** — taken after discontinuation; a major **OS** confounder (crossover, later lines) and the most common [[Intercurrent Event]] in OS analysis.

A bare "anti-cancer therapy used = Yes" flag means little on its own — the load-bearing question is *when* and *at what stage relative to the study drug*, which assigns it to one of the buckets above and decides whether it is a baseline characteristic, a covariate/confounder, or a signal to explain.

Why it matters for analysis: AE attribution (study drug vs concomitant), efficacy purity ([[PSA (Prostate-Specific Antigen)|PSA]]/RECIST/PET), OS interpretation (subsequent therapy), and baseline characterization (prior therapy defines line & refractory status).

By modality these buckets contain different treatment types — surgery, radiotherapy, and systemic drugs including [[Chemotherapy]], targeted/hormone therapy, immunotherapy, and radioligand therapy ([[Lutetium-177 (177Lu)]]).

## Three modalities — systemic vs EBRT vs surgery

Differ by **reach, mechanism, and data type**:

| Modality | Reach | Mechanism | Data |
|---|---|---|---|
| **Systemic therapy** | **whole body** (bloodstream) | a **drug** | `CM` |
| **External beam radiation (EBRT)** | **local** (one site) | radiation from an **external** machine | `PR` |
| **Surgery** | **local** (one site) | physical **removal** | `PR` |

- **Systemic** (系统治疗) = travels everywhere via blood → hits disease anywhere; oral/IV/injection. Includes [[Chemotherapy]], hormonal/endocrine (ADT for prostate), targeted, immunotherapy, and **radioligand** therapy.
- **EBRT** (外照射放疗) = a **procedure**: radiation aimed from a machine (linac) at a **defined area** — e.g. prostate RT, palliative RT to a bone met, SBRT.
- **Surgery** (手术) = a **procedure**: physically **resects** tumour/organ — radical prostatectomy, **orchiectomy** (surgical castration 手术去势), metastasectomy.

**Key caveat:** **radioligand** therapy ([[Lutetium-177 (177Lu)|¹⁷⁷Lu-PSMA]]) *uses* radiation but is **systemic** — the isotope is **injected and travels** to PSMA+ cells everywhere — so it's a **systemic medication, NOT EBRT**. EBRT is the **external-beam (local)** form of radiation.

Prostate tie-in: castration can be **surgical** (orchiectomy) or **medical** (ADT, a systemic drug) — same goal ([[Metastatic Castration-Resistant Prostate Cancer (mCRPC)|castrate testosterone]]), different modality. The prior/concomitant/subsequent **timing** axis is orthogonal — see [[Prior, Concomitant, and Subsequent Treatment]].

