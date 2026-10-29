---
title: "Serious Adverse Event (SAE)"
type: concept
status: learned
created: 2026-06-19
---

# Serious Adverse Event (SAE)

An AE is **serious** (严重不良事件) if it meets **any one** of the regulatory seriousness criteria (ICH E2A / 21 CFR 312.32 — the US Code of Federal Regulations, 美国联邦法规). Only one is needed:

1. Results in **death** (死亡).
2. Is **life-threatening** (危及生命) — the patient was at risk of death *at the time of the event*; not a guess that "it could have been worse".
3. Needs **inpatient hospitalization, or makes an existing stay longer** (prolongation) (住院或延长住院).
4. Results in **persistent or significant disability / incapacity** (持续或显著的残疾/功能丧失).
5. Is a **congenital anomaly / birth defect** (先天异常/出生缺陷).
6. **Important medical event (IME)** (重要医学事件) — a medically important condition that may put the patient in danger (jeopardize, 危及) and may need treatment to prevent one of the outcomes above. The catch-all (兜底条款) for events that are serious but don't match 1–5.

## Serious ≠ severe

The classic trap: **seriousness** (严重性) is a regulatory / outcome category — these 6 criteria — while **severity** (严重程度 / intensity) is the [[CTCAE Grade]]. They are independent:

- A CTCAE **grade 3** event can be **non-serious** (severe, but no SAE criterion met).
- A **grade 1** event can be an **SAE** if, for example, it leads to a hospitalization.

So an event carries a grade (intensity), a seriousness flag (these criteria), and a causality (因果关系) assessment — three separate axes.

## SUSAR — the reportable subset

**SUSAR** = Suspected Unexpected Serious Adverse Reaction (可疑且非预期的严重不良反应) — a **subset of SAE**, made by adding two more filters on top of "serious". Nesting (嵌套): **AE ⊃ SAE ⊃ SAR ⊃ SUSAR**.

1. Start from an **SAE** (a serious AE).
2. **+ Suspected / related** (causality 因果关系) — there is at least a reasonable possibility that the study drug caused it. An SAE judged related = **SAR** (Serious Adverse Reaction); SAEs judged unrelated are not SARs. The words **event vs reaction** give it away: an adverse **event** assumes *nothing* about the cause, while an adverse **reaction** implies a causal link to the drug — so SAR = SAE + causality, nothing else.
3. **+ Unexpected** (非预期) — its nature / severity / frequency is **not** already documented in the **Reference Safety Information (RSI, 参考安全性信息)** — the [[Investigator's Brochure (IB)]] (研究者手册) for an IMP (investigational medicinal product, 试验用药品), or the label / SmPC (summary of product characteristics, 产品特性概要). Reactions already listed are "expected".

So **SUSAR = an SAE that is both related AND unexpected**.

## Reporting flow to the regulatory authority

The **sponsor (申办方) is the hub** (中枢) — sites don't report to authorities directly:

- **Investigator → Sponsor:** the site reports every SAE to the sponsor quickly (usually ≤24 h), with a causality opinion.
- **Sponsor evaluates** each SAE for causality + expectedness (against the RSI). Only the ones that turn out to be **SUSAR** go through the single-case expedited (加急) channel.
- **Sponsor → Regulatory authority** (+ ethics committees / [[IRB and IEC (Ethics Committees)|IRBs/IECs]] + all participating investigators): SUSARs are reported **expedited — 7 days** if fatal/life-threatening, **15 days** otherwise. US = **IND safety report** (IND = investigational new drug application, 新药临床试验申请; 21 CFR 312.32); EU = via **EudraVigilance (EVCTM)**. The single-case report travels on a **CIOMS Form** (the de-facto ICSR form; ICSR = individual case safety report, 个例安全性报告) or its **ICH E2B** electronic equivalent.
- **Aggregate / periodic (汇总/定期):** all SAEs go into the yearly **DSUR** (Development Safety Update Report, 研发期间安全性更新报告) to authorities — so non-SUSAR SAEs are still reported, just periodically, not expedited.

In one line: sites send SAEs in → the sponsor filters them to SUSARs → those go to the authority expedited; everything else is summarized in the DSUR.

## Safety reporting period

The window, defined in the protocol, in which AEs/SAEs must be collected and reported. Exact dates follow the protocol, but the standard shape is:

- **Start** — usually at **informed consent** (知情同意) for SAEs (so events between consent and first dose are captured); routine AE collection often starts at the first dose.
- **End** — a set tail after the **last dose**, commonly **~28–30 days** (longer for biologics with a long half-life, radioligands, etc.). The "+30 days" catches delayed toxicity.
- **Key exception** — a **related** SAE has **no cut-off**: an SAE that the investigator judges as caused by the study drug must be reported **whenever** it appears, even long after the period ends. Causality, not the calendar, decides.
- **Always-report items** — some events (pregnancy, death, second cancer) are reported whatever the period, per protocol.

So collection runs from consent/first dose → last dose + ~30 days, but a *related* SAE stays reportable forever. The grid of when assessments happen is in the [[Schedule of Assessments]].

## The AE lifecycle (related pages)

Seriousness is one step on the path an AE travels — the related pages, in order:

1. **Found** — [[Adverse Event Ascertainment]] (solicited 主动询问 vs spontaneous 自发报告, many sources).
2. **Coded** — the term comes from [[MedDRA]].
3. **Characterized** on independent axes — severity = [[CTCAE Grade]] · **seriousness** = this page · causality (related?) · expectedness vs the RSI in the [[Investigator's Brochure (IB)]].
4. **Managed** — [[Action Taken for an Adverse Event]] (study-drug action + other treatment).
5. **Tracked** — [[Follow-up of Adverse Events]] → final [[Adverse Event Outcome]].
6. **Timed & stored** — onset/end dates, event-driven, in [[SDTM, SDTM IG, and Conformance Rules#Events vs Findings timing — how an AE's occurrence is timed|SDTM (Events vs Findings)]].
7. **Reported** — serious → the seriousness/causality/expectedness filter to SUSAR → [[Serious Adverse Event (SAE)#Reporting flow to the regulatory authority|expedited reporting]], all within the [[Serious Adverse Event (SAE)#Safety reporting period|safety reporting period]].

Different from an [[Adverse Event of Special Interest (AESI)]] (a watch based on interest, defined in advance) and from a [[Dose-Limiting Toxicity (DLT)]] (a dose-finding threshold). A safety concept used across [[Oncology]].
