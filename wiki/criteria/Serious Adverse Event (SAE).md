---
title: "Serious Adverse Event (SAE)"
type: concept
status: learned
tags: [regulatory, trial-conduct, medical]
created: 2026-06-19
updated: 2026-06-19
sources: 4
---

# Serious Adverse Event (SAE)

An AE is **serious** (严重不良事件) if it meets **any one** of the regulatory seriousness criteria (ICH E2A / 21 CFR 312.32). It only takes one:

1. Results in **death** (死亡).
2. Is **life-threatening** (危及生命) — patient was at risk of death *at the time of the event*, not a hypothetical "could have been worse".
3. Requires **inpatient hospitalization or prolongation** of an existing one (住院或延长住院).
4. Results in **persistent or significant disability / incapacity** (持续或显著的残疾/功能丧失).
5. Is a **congenital anomaly / birth defect** (先天异常/出生缺陷).
6. **Important medical event (IME)** (重要医学事件) — a medically important condition that may jeopardize the patient and may require intervention to prevent one of the above. The catch-all for events that are grave but don't tick boxes 1–5.

## Serious ≠ severe

The classic trap: **seriousness** (严重性) is a regulatory/outcome category — these 6 criteria — while **severity** (严重程度 / intensity) is the [[CTCAE Grade]]. They are independent:

- A CTCAE **grade 3** event can be **non-serious** (severe but no SAE criterion met).
- A **grade 1** event can be an **SAE** if, say, it triggers a hospitalization.

So an event carries a grade (intensity), a seriousness flag (these criteria), and a causality assessment — three separate axes.

## SUSAR — the reportable subset

**SUSAR** = Suspected Unexpected Serious Adverse Reaction (可疑且非预期的严重不良反应) — a **subset of SAE** made by stacking two more filters on "serious". Nesting: **AE ⊃ SAE ⊃ SAR ⊃ SUSAR**.

1. Start from an **SAE** (a serious AE).
2. **+ Suspected / related** (causality 因果关系) — at least a reasonable possibility the study drug caused it. An SAE judged related = **SAR** (Serious Adverse Reaction); SAEs judged unrelated are not SARs. The **event vs reaction** wording is the tell: an adverse **event** assumes *nothing* about cause, while an adverse **reaction** implies a causal link to the drug — so SAR = SAE + causality, nothing else.
3. **+ Unexpected** (非预期) — its nature / severity / frequency is **not** already documented in the **Reference Safety Information (RSI)** — the Investigator's Brochure (研究者手册) for an IMP, or the label/SmPC. Already-listed reactions are "expected".

So **SUSAR = SAE that is both related AND unexpected**.

## Reporting flow to the regulatory authority

The **sponsor (申办方) is the hub** — sites don't report to authorities directly:

- **Investigator → Sponsor:** site reports every SAE to the sponsor promptly (typically ≤24 h), with a causality opinion.
- **Sponsor evaluates** each SAE for causality + expectedness (against the RSI). Only the ones that come out **SUSAR** get the single-case expedited channel.
- **Sponsor → Regulatory authority** (+ ethics committees/IRBs + all participating investigators): SUSARs reported **expedited — 7 days** fatal/life-threatening, **15 days** other. US = **IND safety report** (21 CFR 312.32); EU = via **EudraVigilance (EVCTM)**.
- **Aggregate / periodic:** all SAEs roll into the annual **DSUR** (Development Safety Update Report) to authorities — so non-SUSAR SAEs are still reported, just periodically, not expedited.

In one line: sites send SAEs in → sponsor filters to SUSARs → those go to the authority expedited, everything else aggregated in the DSUR.

## Safety reporting period

The protocol-defined window in which AEs/SAEs must be collected and reported. Exact dates are per protocol, but the standard shape:

- **Start** — usually at **informed consent** (知情同意) for SAEs (so events between consent and first dose are captured); routine AE collection often starts at first dose.
- **End** — a defined tail after the **last dose**, commonly **~28–30 days** (longer for long-half-life biologics, radioligands, etc.). The "+30 days" catches delayed toxicity.
- **Key exception** — a **related** SAE has **no cut-off**: an SAE the investigator assesses as causally related to study drug is reportable **whenever** it surfaces, even long after the period ends. Causality, not the calendar, governs.
- **Always-report items** — some events (pregnancy, death, secondary malignancy) are reported irrespective of period, per protocol.

So collection runs consent/first-dose → last-dose + ~30 days, but a *related* SAE stays reportable indefinitely. The grid of when assessments happen lives in the [[Schedule of Assessments]].

Distinct from an [[Adverse Event of Special Interest (AESI)]] (pre-specified interest-based watch) and from a [[Dose-Limiting Toxicity (DLT)]] (dose-finding threshold). AE terms come from [[MedDRA]]. A cross-cutting safety concept in [[Oncology]].
