---
title: "Anti-Cancer Therapy Categories in Oncology Trials"
type: concept
status: learned
created: 2026-06-11
---

# Anti-Cancer Therapy Categories in Oncology Trials

In an oncology trial, treatments aimed at the cancer are sorted into non-overlapping groups ("buckets") by their **role relative to the study drug**. The study drug is the studied "independent variable" (自变量); every other anti-cancer therapy is a confounder (混杂因素) to control or explain.

In pharmacology terms (药理学上), the study drug *is* a type of anti-cancer therapy — the groups below are a **trial-data distinction**, not a biological one.

- **Study drug / Investigational Product (IP, 试验用药品)** — the single product being tested for safety/efficacy. SDTM **EX** (exposure; EC if needed).
- **Prior anti-cancer therapy** (既往抗肿瘤治疗) — treatments before enrollment. Drives eligibility, washout (洗脱期), line of therapy (治疗线), and refractory status (难治状态). SDTM **CM** (concomitant medications; drugs) / **PR** (procedures; radiation, surgery).
- **Concomitant anti-cancer therapy** (合并抗肿瘤治疗) — usually *not allowed* (prohibited) during the study. If it happens, it muddies (contaminates) whether efficacy/safety comes from the study drug (attribution, 归因) — often a protocol deviation (方案偏离).
- **Subsequent anti-cancer therapy** (后续抗肿瘤治疗) — taken after stopping the study drug; a major **OS** (overall survival, 总生存期) confounder (crossover 交叉, later lines) and the most common [[Intercurrent Event]] in OS analysis.

A simple "anti-cancer therapy used = Yes" flag means little by itself. The key question is *when*, and *at what stage relative to the study drug*. That puts it into one of the groups above, and decides whether it is a baseline characteristic, a covariate/confounder, or a signal to explain.

Why it matters for analysis: AE attribution (study drug vs concomitant), clean efficacy readouts ([[PSA (Prostate-Specific Antigen)|PSA]]/RECIST/PET), OS interpretation (subsequent therapy), and describing the baseline (prior therapy defines line and refractory status).

By modality (治疗方式), these groups hold different treatment types — surgery, radiotherapy, and systemic drugs including [[Chemotherapy]], targeted/hormone therapy, immunotherapy, and radioligand therapy ([[Lutetium-177 (177Lu)]]).

## Three modalities — systemic vs EBRT vs surgery

They differ by **reach, mechanism, and data type**:

| Modality | Reach | Mechanism | Data |
|---|---|---|---|
| **Systemic therapy** | **whole body** (bloodstream, 血流) | a **drug** | `CM` |
| **External beam radiation (EBRT)** | **local** (one site) | radiation from an **external** machine | `PR` |
| **Surgery** | **local** (one site) | physical **removal** | `PR` |

- **Systemic** (系统治疗/全身治疗) = travels everywhere in the blood → hits disease anywhere; by mouth / IV / injection. Includes [[Chemotherapy]], hormonal/endocrine (ADT for prostate), targeted, immunotherapy, and **radioligand** therapy.
- **EBRT** (外照射放疗) = a **procedure**: radiation aimed from a machine (linac, 直线加速器) at a **defined area** — e.g. prostate RT (radiotherapy), palliative (姑息性) RT to a bone met, SBRT (stereotactic body radiotherapy, 立体定向放疗).
- **Surgery** (手术) = a **procedure** that physically **removes** (resects, 切除) tumour/organ — radical prostatectomy (根治性前列腺切除术), **orchiectomy** (睾丸切除术 = surgical castration 手术去势), metastasectomy (转移灶切除术).

**Key caveat (注意):** **radioligand** therapy ([[Lutetium-177 (177Lu)|¹⁷⁷Lu-PSMA]]) *uses* radiation but is **systemic** — the isotope (同位素) is **injected and travels** to PSMA+ cells everywhere — so it is a **systemic medication, NOT EBRT**. EBRT is the **external-beam (local)** form of radiation.

Prostate tie-in: castration can be **surgical** (orchiectomy) or **medical** (ADT, a systemic drug) — same goal ([[Metastatic Castration-Resistant Prostate Cancer (mCRPC)|castrate testosterone]]), different modality. The prior/concomitant/subsequent **timing** axis is a separate, independent axis (orthogonal, 正交) — see [[Prior, Concomitant, and Subsequent Treatment]].
