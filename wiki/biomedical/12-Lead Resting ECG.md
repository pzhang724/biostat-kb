---
title: "12-Lead Resting ECG"
type: concept
status: learned
tags: [medical, trial-conduct]
created: 2026-06-18
updated: 2026-06-19
sources: 5
---

# 12-Lead Resting ECG

Standard electrocardiogram (12导联静息心电图) recording the heart's electrical activity from 12 leads (angles), taken at rest.

- In trials it is a **cardiac safety assessment** — screens for arrhythmia / conduction abnormalities and measures intervals, notably **QT/QTc** (the basis for the QTc eligibility cap on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]]).
- **"Resting"** distinguishes it from exercise / stress ECG.

**Why "12-lead" (12导联):** 12 = 12 electrical **viewing angles** of the same heart (from 10 electrodes), not 12 machines — 6 limb leads (I, II, III, aVR, aVL, aVF; frontal plane) + 6 precordial leads (V1–V6; horizontal plane). One lead sees only one direction and can miss a region-specific change; multiple angles let you both **detect and localize** an abnormality to a wall (anterior/inferior/lateral/septal), spot chamber enlargement, and place a conduction block. It is the standard **complete diagnostic** ECG, vs a 1–3-lead rhythm strip/telemetry that only tracks rate & rhythm. Trials specify it because the QT/QTc cardiac-safety read and the **ICH E14** (thorough-QT) framework are built on standardized full 12-lead recordings — complete, reproducible, comparable visit-to-visit and across sites.

## QT / QTc and its CTCAE grading

- **QT interval (QT间期)** = from the start of the Q wave to the end of the T wave = one beat's ventricular depolarization + repolarization. It **shortens as heart rate rises**, so it is rate-**corrected** → **QTc (校正QT间期)** (Bazett QTcB / Fridericia QTcF; trials usually prefer **QTcF**).
- **Why it matters:** a long QTc = delayed repolarization → risk of **torsades de pointes (尖端扭转型室速, TdP)**, a polymorphic VT that can degenerate to VF / sudden death. Many oncology drugs prolong QT, so QTc is a standard cardiac-safety signal.
- **CTCAE grading** (see [[CTCAE Grade]]): G1 450–480 ms · G2 481–500 ms · **G3 ≥501 ms or >60 ms change from baseline** · G4 torsades / polymorphic VT / serious-arrhythmia signs. So **"Grade 3 QTc"** = reached ≥501 ms (or jumped >60 ms) but **without** the arrhythmia event that defines G4 — the "severe / must act" line: dose interruption, repeat ECG, check K/Mg/Ca, review QT-prolonging con-meds. The **QTc entry cap** (e.g. QTcF ≤480 ms) on [[Eligibility and Safety Parameters (PSMA Radioligand Trial)]] is the screen that keeps such patients out; on-study it can count toward a [[Dose-Limiting Toxicity (DLT)|DLT]].

**Triplicate ECG (三次重复心电图):** taking **three** 12-lead ECGs in quick succession (~1–2 min apart, patient resting) at the *same* nominal timepoint and **averaging** the QT/QTc across them. QTc has beat-to-beat and minute-to-minute biological + measurement variability, so averaging 3 yields a more precise, reproducible value. Standard for QT cardiac-safety / **ICH E14** assessment; protocols often specify triplicates at each ECG timepoint, frequently **time-matched to [[Pharmacokinetics (PK)|PK]] sampling** so QTc can be related to drug concentration (exposure–response / concentration–QTc).

**Local vs central reading:** like imaging, trial ECGs can be read **locally** (本地判读 — by the site/investigator, for immediate safety and the screening eligibility check: arrhythmia present? QTc over the entry cap?) or sent to a **central ECG core lab** (中心心电图核心实验室) for standardized, blinded, often computer-assisted interval measurement — especially QT/QTc. Central reading reduces inter-site variability and bias; since QTc is a regulated cardiac-safety endpoint, the formal analysis typically uses the central read. Same idea as **BICR** for imaging (see [[Radiological Assessment]]); many trials use both — local for real-time safety, central for the analysis dataset.

A cross-cutting safety assessment in [[Oncology]].
