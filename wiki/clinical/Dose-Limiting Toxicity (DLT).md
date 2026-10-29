---
title: "Dose-Limiting Toxicity (DLT)"
type: concept
status: learned
created: 2026-06-18
---

# Dose-Limiting Toxicity (DLT)

**Dose-Limiting Toxicity (DLT, 剂量限制性毒性)** — a severe adverse event that the protocol defines in advance (pre-specified, 预先规定的). If it happens, the dose is considered too toxic, and it "limits" further dose escalation (剂量递增). It is the unit of *unacceptable toxicity* that the whole dose-finding (剂量探索) machinery is built on.

- **Definition** — set in each protocol; usually drug-related (drug-attributable, 与药物相关) [[CTCAE Grade|CTCAE]] **Grade ≥3 non-hematologic** (非血液学) or **Grade ≥4 hematologic** (血液学) toxicities, with exceptions (toxicities that are manageable or short-lived, transient 一过性, may be excluded). Coded with [[MedDRA]].
- **DLT window (DLT 评估期)** — DLTs are counted within a defined evaluation period, usually the **first treatment cycle** (e.g. the first 21/28 days).
- **Drives escalation** — the **DLT rate** in a dose cohort (剂量组) decides whether to escalate / stay / de-escalate (降低剂量). The [[MTD and RP2D|MTD]] (maximum tolerated dose, 最大耐受剂量) is the highest dose that keeps the DLT rate below the target (commonly ~33%).

**In one line:** DLT is the red line — step on it and the dose is judged too toxic. 3+3 / CRM (continual reassessment method, 连续重评估法) / BOIN (Bayesian optimal interval, 贝叶斯最优区间设计) / [[MTD and RP2D|EWOC]] all find the MTD by tracking the DLT rate.

## Non-hematologic DLT & Hy's law (example wording)

A protocol may define the **non-hematologic** DLT as **Grade ≥3** (with exceptions), *plus* a specific liver-injury signal — a **Hy's law case** (海氏法则病例), defined as all of:

- **AST or ALT > 3× ULN** (aspartate / alanine aminotransferase, 天冬氨酸 / 丙氨酸氨基转移酶; ULN = upper limit of normal, 正常值上限) — **hepatocellular injury** (肝细胞损伤): liver cells are damaged and their enzymes (酶) leak out; **AND**
- **total bilirubin (总胆红素) > 2× ULN** — the liver's excretory (排泄) function is failing (jaundice, 黄疸): real loss of function, not just an enzyme leak; **AND**
- **alkaline phosphatase (ALP, 碱性磷酸酶) < 2× ULN** — rules out **cholestasis** / blocked bile ducts (biliary obstruction, 胆汁淤积/胆道梗阻) as the cause of the bilirubin rise, confirming the damage is hepatocellular; **AND**
- **no other reason for liver injury** (viral hepatitis 病毒性肝炎, alcohol, other drugs that harm the liver…) — so the trial drug is the likely cause (culprit, 元凶).

**Why it matters:** "real liver-cell damage + the liver cannot clear bilirubin + no blockage or other explanation" is a strong warning sign (ominous predictor, 凶险的预测信号) of severe or fatal **drug-induced liver injury (DILI, 药物性肝损伤)**. Even a couple of Hy's law cases in a drug program is a major safety red flag, so it counts automatically as a DLT. (For the labs see AST/ALT and bilirubin on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]; severity via [[CTCAE Grade]].)

A rule used across [[Oncology]].
