---
title: "Intercurrent Event"
type: concept
status: learned
created: 2026-06-11
---

# Intercurrent Event

An **intercurrent event (ICE, 伴发事件)** is a core idea of the **ICH E9(R1)** estimand framework (估计目标框架): an event that happens *after treatment starts* and affects either the **interpretation** or the **existence** of the outcome measurement. It is not a plain covariate and not missing data — after an ICE, the quantity you planned to measure changes its meaning.

Typical ICEs: stopping or switching treatment (discontinuation or switching), use of prohibited/rescue concomitant medication (合并用药), **subsequent anti-cancer therapy**, and death (for endpoints other than survival). Stopping treatment corresponds to [[End of Treatment vs End of Study|End of Treatment]] — the patient goes off treatment but is usually still followed up to [[End of Treatment vs End of Study|End of Study]].

E9(R1) requires you to pre-specify, for each type of ICE, one of five **handling strategies**:

- **Treatment policy** (疗法策略) — ignore the ICE; use the observed outcome whatever happened (the spirit of intention-to-treat, 意向性治疗).
- **Hypothetical** (假想策略) — imagine the outcome if the ICE had not happened (e.g. censor at the event).
- **Composite** (复合策略) — build the ICE into the endpoint definition (e.g. count it as a failure).
- **While on treatment** (治疗期间策略) — use only the outcome up to the ICE.
- **Principal stratum** (主分层策略) — estimate within the subpopulation that would not have the ICE.

The choice of strategy, together with population, endpoint and summary measure, defines the [[Estimand]]. In oncology, subsequent anti-cancer therapy (see [[Anti-Cancer Therapy Categories in Oncology Trials]]) is the most common ICE in **OS** (overall survival) analysis: a treatment-policy strategy keeps following OS as usual, while a hypothetical strategy censors at the switch.
