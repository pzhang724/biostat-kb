---
title: "Radiological Assessment"
type: concept
status: learned
created: 2026-06-18
---

# Radiological Assessment

**Radiological assessment (影像学评估)** — judging disease with medical **imaging** (CT, [[MRI (Magnetic Resonance Imaging)|MRI]], bone scan, [[PET (Positron Emission Tomography)|PET]] / [[PSMA PET-CT]], etc.): measuring tumour burden (肿瘤负荷), finding and measuring lesions, and judging response or progression. In oncology trials it is the imaging-based read (判读) of disease status that **feeds the response criteria** ([[RECIST 1.1]], [[PCWG3 Criteria]], the [[Modified RECIST 1.1 and PCWG3 Criteria]]) → [[Best Overall Response|overall response]], progression, rPFS.

- One of three assessment types — different from **clinical** assessment (symptoms/exam) and **lab / biomarker** assessment (e.g. [[PSA (Prostate-Specific Antigen)|PSA]]). "Radiological" means imaging specifically.
- Done at timepoints set in the protocol (the scan schedule).
- Often read by **BICR** (blinded independent central review, 独立中心盲态阅片), not only by the local investigator, to reduce bias.
- **Radiological progression (影像学进展)** is the progression event defined by imaging — the basis of **rPFS** (radiographic progression-free survival, 影像学无进展生存期).

**Why one criterion still gives different reads** — the standard is a rule, but using it needs human **judgment calls** (主观判断) that are not fully fixed (deterministic, 确定性的), so the same rule read by different people gives different results. In tumour imaging (RECIST): which lesions to pick as **target lesions** (up to 5); where to draw the diameter (which slice 层面, where to put the caliper 测量卡尺, partial-volume effect 部分容积效应); and whether something is a **new lesion** or **progression** at the borderline (~20% growth, image quality, artifact 伪影). In **ECG/QTc**: where to put the **end of the T wave** (T-wave offset — well known to depend on the reader), manual vs algorithm, which leads/beats, baseline noise. On top of this **variability** (变异) there is **bias** (偏倚): a local reader is often not blinded (knows the treatment arm, and has real-time treatment pressures), while central is blinded, standardized, and works from the complete dataset. **This applies wherever a human read or measurement sits between the raw data and the categorical result** — tumour imaging, ECG, also central pathology (病理), bone scans, echo (超声心动图), photographs. The more objective/automated the measure, the smaller the gap.

**When local and central disagree** — disagreement (discordance, 不一致) is common and expected. Note it is **one criterion, two independent reads**: local and central apply the *same* rules (e.g. RECIST 1.1 / the same QTc threshold); what differs is *who reads*. It is not two competing standards. Both are kept in the dataset; the protocol says in advance which one is primary, and the two serve different purposes:

- **Patient management follows local** — decisions to treat / stop, and real-time safety, cannot wait for central, so the site read drives care.
- **The statistical analysis follows central** — regulated efficacy/safety endpoints (progression, rPFS, QTc) use the blinded central read as the primary analysis, for consistency across sites and less bias.
- Discordance is **measured and managed**: BICR often uses **two independent readers + a third adjudicator** (裁决者; adjudication 裁决); the **discordance rate** is examined; systematic bias (e.g. evaluation-time bias 评估时间偏倚 from coming off treatment on the local read) is checked with **sensitivity analyses** (敏感性分析) and censoring rules (删失规则).
- A large discordance is mainly a **bias / credibility** (可信度) signal, not just a data-quality issue. Central reading exists partly to **check (audit) the local read for bias** (especially in open-label 开放标签 trials, where the investigator knows the arm). Agreement → reassurance; a big systematic difference → trust central (primary) and find out why (this *may* include reader quality / retraining, but the core question is whether the endpoint is credible).

**In one line:** it's not "who is right" — local decides how the patient is treated, central decides how the data are counted. The protocol names the primary read (usually central) and stress-tests (压力测试) the disagreement.

What it measures comes from the [[Measurable vs Non-Measurable Disease (RECIST)|measurability rules]]. An assessment used across [[Oncology]].
