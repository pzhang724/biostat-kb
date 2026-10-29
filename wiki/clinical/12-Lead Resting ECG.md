---
title: "12-Lead Resting ECG"
type: concept
status: learned
created: 2026-06-18
---

# 12-Lead Resting ECG

A standard electrocardiogram (12导联静息心电图) that records the heart's electrical activity from 12 leads (导联; viewing angles), taken at rest.

- In trials it is a **cardiac safety assessment** (心脏安全性评估) — it checks for arrhythmia (心律失常) / conduction (传导) abnormalities and measures intervals (间期), especially **QT/QTc** (the basis for the QTc entry cap on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]).
- **"Resting"** separates it from an exercise / stress ECG (运动/负荷心电图).

**Why "12-lead" (12导联):** 12 = 12 electrical **viewing angles** of the same heart (from 10 electrodes, 电极), not 12 machines: 6 limb leads (肢体导联; I, II, III, aVR, aVL, aVF; frontal plane 额面) + 6 precordial leads (胸前导联; V1–V6; horizontal plane 水平面). One lead sees only one direction and can miss a change in one region. Many angles let you both **detect and localize** (定位) an abnormality to a wall of the heart (anterior 前壁 / inferior 下壁 / lateral 侧壁 / septal 间隔), spot chamber enlargement (心腔扩大), and place a conduction block. It is the standard **complete diagnostic** ECG, compared with a 1–3-lead rhythm strip / telemetry (遥测) that only tracks rate and rhythm. Trials specify it because the QT/QTc cardiac-safety read and the **ICH E14** (thorough QT, 全面 QT 研究) framework are built on standardized full 12-lead recordings — complete, reproducible, and comparable visit to visit and across sites.

## QT / QTc and its CTCAE grading

- **QT interval (QT间期)** = from the start of the Q wave to the end of the T wave = the ventricles' depolarization (去极化) + repolarization (复极化) for one beat. It **gets shorter as heart rate goes up**, so it is **corrected** for rate → **QTc (校正QT间期)** (Bazett QTcB / Fridericia QTcF; trials usually prefer **QTcF**).
- **Why it matters:** a long QTc = delayed repolarization → risk of **torsades de pointes (尖端扭转型室速, TdP)**, a polymorphic VT (ventricular tachycardia, 多形性室性心动过速) that can turn into VF (ventricular fibrillation, 心室颤动) / sudden death. Many oncology drugs prolong QT, so QTc is a standard cardiac-safety signal.
- **CTCAE grading** (see [[CTCAE Grade]]): G1 450–480 ms · G2 481–500 ms · **G3 ≥501 ms or >60 ms change from baseline** · G4 torsades / polymorphic VT / signs of serious arrhythmia. So **"Grade 3 QTc"** = reached ≥501 ms (or jumped >60 ms) but **without** the arrhythmia event that defines G4 — the "severe / must act" line: interrupt the dose, repeat the ECG, check K/Mg/Ca (potassium 钾 / magnesium 镁 / calcium 钙), and review QT-prolonging con-meds (合并用药). The **QTc entry cap** (e.g. QTcF ≤480 ms) on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]] is the screen that keeps such patients out; during the study it can count toward a [[Dose-Limiting Toxicity (DLT)|DLT]].

**Triplicate ECG (三次重复心电图):** taking **three** 12-lead ECGs quickly one after another (~1–2 min apart, patient resting) at the *same* nominal (名义) timepoint, and **averaging** the QT/QTc across them. QTc varies beat to beat and minute to minute (biological + measurement variability), so the average of 3 gives a more precise, reproducible value. Standard for QT cardiac-safety / **ICH E14** assessment. Protocols often specify triplicates at each ECG timepoint, often **time-matched to [[Pharmacokinetics (PK)|PK]] sampling**, so QTc can be related to drug concentration (exposure–response / concentration–QTc, 浓度-QTc 分析).

**Do vital signs need triplicate too?** Not usually — triplicate is the standard practice for **ECG**. Among vital signs, **blood pressure** is the one sometimes taken twice or three times (3 readings after rest, averaged) to reduce variability, especially for drugs that affect BP or when BP is a focus. Other vitals (HR heart rate, temperature, RR respiratory rate, SpO₂ oxygen saturation 血氧饱和度) are usually taken **once**. It is **set by the protocol**, not universal. Each repeat is recorded with a **replicate number** (`VSREPNUM` for VS, `EGREPNUM` for EG) and averaged in ADaM.

**Local vs central reading:** like imaging, trial ECGs can be read **locally** (本地判读 — by the site/investigator, for immediate safety and the screening eligibility check: is there an arrhythmia? is QTc over the entry cap?) or sent to a **central ECG core lab** (中心心电图核心实验室) for standardized, blinded, often computer-assisted interval measurement — especially QT/QTc. Central reading reduces variability between sites and bias. Since QTc is a regulated cardiac-safety endpoint, the formal analysis usually uses the central read. Same idea as **BICR** for imaging (see [[Radiological Assessment]]); many trials use both — local for real-time safety, central for the analysis dataset.

A safety assessment used across [[Oncology]].
