---
title: "Eligibility and Safety Parameters (PSMA Radioligand Trial)"
type: concept
status: learned
tags: [medical, trial-conduct]
created: 2026-06-18
updated: 2026-06-18
sources: 4
---

# Eligibility and Safety Parameters (PSMA Radioligand Trial)

The eligibility / safety screen of a PSMA-targeted radioligand prostate-cancer trial. Labs confirm organ-function adequacy and drive on-treatment monitoring; the conditions are mostly exclusion criteria. Several — kidney (creatinine), bladder (cystitis), salivary glands (xerostomia), marrow (MDS) — map to where the radioligand deposits dose.

## Lab / ECG safety & eligibility parameters (organ function)

Two classes: four "reserve / synthesis" markers want **high** (entry floor); five "injury / toxicity" markers want **low** (entry cap).

| English | 中文 | 高好/低好 | Entry | Why |
|---|---|---|---|---|
| Absolute neutrophil count (ANC) | 中性粒细胞绝对计数 | 高好 high | floor 下限 | low = neutropenia → infection (often ≥1.5×10⁹/L) |
| Hemoglobin (Hgb) | 血红蛋白 | 高好 high | floor 下限 | low = anemia |
| Platelets | 血小板 | 高好 high | floor 下限 | low = thrombocytopenia → bleeding |
| Serum albumin | 血清白蛋白 | 高好 high | floor 下限 | low = poor liver synthesis / nutrition / prognosis |
| AST (aspartate aminotransferase) | 天冬氨酸氨基转移酶 (谷草转氨酶) | 低好 low | cap 上限 | high = hepatocellular injury (≤2.5–3× ULN) |
| ALT (alanine aminotransferase) | 丙氨酸氨基转移酶 (谷丙转氨酶) | 低好 low | cap 上限 | high = hepatocellular injury |
| Total bilirubin | 总胆红素 | 低好 low | cap 上限 | high = poor excretion / cholestasis (≤1.5× ULN) |
| Creatinine | 肌酐 | 低好 low | cap 上限 | high = poor renal function (kidney is dose-limiting for radioligand) |
| QT interval | QT间期 | 低/短好 low | cap 上限 | long = arrhythmia (torsades) risk |
| QTc | 校正QT间期 (按心率校正) | 低/短好 low | cap 上限 | same, rate-corrected (e.g. QTcF ≤480 ms) |

Grouping by organ: ANC/Hgb/platelets = hematology (marrow reserve); albumin/AST/ALT/bilirubin = liver; creatinine = kidney; QT/QTc = cardiac.

**口诀 (mnemonic):** 身体"产出/储备"的 → 越高越好 (floor)；"损伤/废物"标志 → 越低越好 (cap)。
> **「血、蛋白 要高；肝、肾、心电 要低。」**
> - 要高 (floors): 血 = 三系血细胞 (ANC / Hgb / Plt)、蛋白 = 白蛋白 — 身体造出来、要够用的。
> - 要低 (caps): 肝 = AST / ALT / 胆红素、肾 = 肌酐、心电 = QT / QTc — 损伤/废物/危险信号，越少越好。
>
> 一层加深：白蛋白是肝"合成"的→要高；AST/ALT/胆红素是肝"损伤"的标志→要低。同是肝，合成高好、损伤低好。

## Relevant / exclusion conditions

No high/low direction here — these are **presence = excluded** (有则排除).

- **Cystitis, infective (感染性膀胱炎)** — bladder inflammation; relevant as the radioligand is excreted via the urinary tract.
- **PSMA-targeted radioconjugate (PSMA靶向放射偶联物)** — the therapy itself: a PSMA-binding ligand linked to a radioisotope (radioligand therapy); not a lab parameter. Same target as [[PSMA PET-CT]] (theranostic pair).
- **Systemic anti-cancer therapy (全身性抗癌治疗)** — prior/concurrent systemic treatment; washout & exclusion. See [[Anti-Cancer Therapy Categories in Oncology Trials]].
- **Symptomatic (spinal) cord compression (症状性脊髓压迫)** — oncologic emergency from epidural metastases; exclusion.
- **Hypersensitivity (超敏反应)** — allergy to drug/excipients; exclusion.
- **Xerostomia (口干)** — dry mouth; salivary glands express PSMA, so PSMA radioligands cause off-target salivary uptake/toxicity → xerostomia.
- **Cardiac disease (心脏疾病)** — e.g. recent MI, heart failure, significant arrhythmia; exclusion (ties to QT/QTc above).
- **Thromboembolic or cerebrovascular events (血栓栓塞或脑血管事件)** — recent DVT/PE/stroke/TIA; exclusion.
- **Malignancy (其他恶性肿瘤)** — second/other primary malignancy; excluded unless disease-free for a stated period.
- **Myelodysplastic syndrome (MDS, 骨髓增生异常综合征)** — pre-leukemic marrow disorder; especially relevant for radioligand therapy, where marrow radiation risks secondary MDS/AML.

## Relationship to prostate cancer

The labs themselves are **generic oncology** safety parameters (in nearly every trial), not prostate-specific. Their prostate-cancer relevance runs through two channels:

**Disease biology & population**
- **Bone-dominant metastasis → marrow infiltration**: anemia (Hgb↓), thrombocytopenia, neutropenia, reduced marrow reserve; spine metastases → symptomatic cord compression (a real prostate-cancer complication).
- **Elderly, comorbid men (often on ADT)**: cardiac disease, QT/QTc, and thromboembolic/cerebrovascular events more prevalent; albumin reflects performance status / prognosis.

**PSMA radioligand mechanism (the modality, used in mCRPC)**
- Renal excretion + kidney is dose-limiting → **creatinine**.
- Salivary glands express PSMA → off-target uptake → **xerostomia** (signature toxicity).
- Urinary excretion + prostate/bladder proximity → **cystitis / bladder**.
- Marrow irradiation (bone mets concentrate the radioligand near marrow) → **cytopenias + secondary MDS/AML**.

Prostate-specific prior lines (ADT, ARPIs like abiraterone/enzalutamide, taxane chemo) define the systemic-anti-cancer-therapy washout — see [[Anti-Cancer Therapy Categories in Oncology Trials]].

**Bottom line:** generic thresholds, but two things sharpen them in prostate cancer — a bone-metastatic, elderly, comorbid population (marrow + cardiac + frailty), and the PSMA-radioligand mechanism (kidney, salivary, bladder, marrow are exactly where the radiation lands).

Part of [[Oncology]]; radioligand dosing context in [[Pharmacokinetics (PK)]] / [[Dosimetry]].
