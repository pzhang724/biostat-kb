---
title: "Dose-Limiting Toxicity (DLT)"
type: concept
status: learned
tags: [trial-conduct, medical, statistics]
created: 2026-06-18
updated: 2026-06-18
sources: 2
---

# Dose-Limiting Toxicity (DLT)

**Dose-Limiting Toxicity (DLT, 剂量限制性毒性)** — a pre-specified, protocol-defined severe adverse event that, if it occurs, means the dose is considered too toxic and "limits" further dose escalation. It is the unit of *unacceptable toxicity* the whole dose-finding machinery is built on.

- **Definition** — set per protocol, typically drug-attributable [[CTCAE Grade|CTCAE]] **≥3 non-hematologic** or **≥4 hematologic** toxicities (with exceptions — manageable/transient ones may be excluded). Coded via [[MedDRA]].
- **DLT window (评估期)** — counted within a defined evaluation period, usually the **first treatment cycle** (e.g. first 21/28 days).
- **Drives escalation** — the **DLT rate** in a dose cohort decides escalate / hold / de-escalate; the [[MTD and RP2D|MTD]] is the highest dose keeping the DLT rate below target (commonly ~33%).

**In one line:** DLT is the red line — step on it and the dose is judged too toxic. 3+3 / CRM / BOIN / [[MTD and RP2D|EWOC]] all find the MTD by tracking the DLT rate.

## Non-hematologic DLT & Hy's law (example wording)

A protocol may define the **non-hematologic** DLT as **Grade ≥3** (with exceptions), *plus* a specific liver-injury signal — a **Hy's law case**, defined as all of:

- **AST or ALT > 3× ULN** (upper limit of normal) — **hepatocellular injury** (肝细胞损伤): liver cells damaged, enzymes leak out; **AND**
- **total bilirubin > 2× ULN** — the liver's excretory function is failing (jaundice, 黄疸): real functional impairment, not just enzyme leak; **AND**
- **alkaline phosphatase (ALP, 碱性磷酸酶) < 2× ULN** — rules out **cholestasis** / biliary obstruction (胆汁淤积) as the cause of the bilirubin rise, confirming it is hepatocellular; **AND**
- **no other reason for liver injury** (viral hepatitis, alcohol, other hepatotoxic drugs…) — so the trial drug is the likely culprit.

**Why it matters:** "real hepatocyte damage + the liver failing to clear bilirubin + not explained by blockage or anything else" is an ominous predictor of severe/fatal **drug-induced liver injury (DILI, 药物性肝损伤)** — even a couple of Hy's law cases in a program is a major safety red flag, so it counts automatically as a DLT. (Labs cf. AST/ALT, bilirubin on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]; severity via [[CTCAE Grade]].)

A cross-cutting rule in [[Oncology]].
