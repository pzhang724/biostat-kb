---
title: "Best Overall Response"
type: concept
status: learned
created: 2026-06-11
---

# Best Overall Response

The key idea: **however complex the criterion is, at a single timepoint a patient has exactly ONE response status — and the "best" is the best among all those timepoint statuses.** This is the two-level structure behind response endpoints.

- **Timepoint (visit) response** — at each assessment the criterion (e.g. [[Modified RECIST 1.1 and PCWG3 Criteria]], or plain [[RECIST 1.1]]) reduces (collapses) everything — target, non-target, new lesions, bone — into **one** status: **CR / PR / SD / PD / NE**.
- **Best Overall Response (BOR, 最佳总体缓解)** — the single **best** status recorded across **all** timepoints, from baseline until progression/death/end of follow-up. Order: **CR > PR > SD > PD** (NE is handled separately). "The best among all of these" = take the maximum over the sequence of visits. **Yes, it is the running best-so-far** (截至当前的最佳) — at any visit, BOR = the best among that visit + all earlier ones. The final reported BOR is that cumulative best over the whole **baseline → first PD** window (you cannot pick up a better response after progression), subject to the confirmation / SD-duration rules below.

## Ordering, best → worst

By tumour burden / how favourable it is:

> **CR ≈ NED  >  PR  >  SD  >  PD**  — and **NE sits outside the ordering**.

- **CR** (Complete Response, 完全缓解) — all known disease is gone (best).
- **NED** (No Evidence of Disease, 无疾病证据) — no disease can be detected; ranks **together with CR**. But it is a **clinical / post-surgical** term (the patient was made disease-free by surgery, resection 切除, or entered with no measurable disease), **not** a standard [[RECIST 1.1]] timepoint category — RECIST uses **CR**. It shows up in CDISC controlled terminology (受控术语) for response and in adjuvant (辅助治疗) settings.
- **PR** (Partial Response, 部分缓解) — large shrinkage (≥30% in SoD, sum of diameters).
- **SD** (Stable Disease, 疾病稳定) — neither PR nor PD.
- **PD** (Progressive Disease, 疾病进展) — growth / new lesions (worst).
- **NE** (Not Evaluable, 不可评估) — the assessment could not be made (missing/inadequate). It is **not** better or worse — it means "unknown", so it is **off** the favourability scale (handled separately below).

**Non-CR/Non-PD** (often shortened to "Non-PD") is the **SD-equivalent for non-target / non-measurable disease**. Non-target lesions are judged **qualitatively** (present / absent / clearly worse), not by the ≥30% / ≥20% size thresholds, so you cannot properly call PR or SD on them. The in-between state is "**not CR** (lesion / tumour marker still present) **and not PD** (no clear progression)". Order: **CR > Non-CR/Non-PD (≈ SD) > PD**. For a patient whose baseline disease is **non-measurable only**, the set of timepoint responses becomes **CR / Non-CR/Non-PD / PD / NE** — no PR and no SD (both need a measurable change); Non-CR/Non-PD takes the place of SD. See [[RECIST 1.1]].

**Why NED exists as its own category:** because some patients have **no measurable disease that could respond**, so CR cannot apply. CR means that measurable disease you *had* disappeared (a treatment response). If there were no lesions to begin with, "CR" is logically impossible — the state is "still no detectable disease" = NED. Two settings drive it: (1) **adjuvant trials** — after curative surgery the patient is disease-free but at risk of recurrence (复发), and the drug prevents recurrence. There is no measurable target, so no ORR/CR, and the endpoint is **DFS** (disease-free survival, 无病生存; baseline = NED, event = recurrence); (2) **surgical conversion** (手术转化) — a patient made NED by removing the metastases with surgery. That is not an imaging response caused by the drug, so calling it CR would wrongly give the drug the credit. So NED separates "no disease to assess / disease-free by other means" from a real response (CR/PR) — counting NED reached by surgery as a response would inflate (夸大) / confound ORR.

**Why such patients are *included* at all** — two routes: (1) **by design** — in an adjuvant trial the disease-free patients **are** the target population (the question is preventing recurrence, not shrinkage), so including them is the whole point, and NED just labels their state through the study; (2) **by ITT** (intention-to-treat, 意向性治疗) — in a trial of measurable disease, a patient who becomes NED during the study (e.g. surgery removes the disease) was validly enrolled at baseline, and **intention-to-treat** keeps you tracking them to the end instead of deleting them, so that timepoint is recorded as NED. (Whether they still count in the strict ORR / response-evaluable set is decided separately, by the baseline-measurable-disease rule.)

Rules that limit the maximum:

- **Confirmation** — in trials where ORR is primary / that are not randomized, a CR or PR must be **confirmed** by a repeat assessment ≥4 weeks later, or it does not count as the BOR.
- **Minimum SD duration** — SD only qualifies after a minimum interval from baseline set in the protocol (e.g. ≥6–8 weeks); an earlier "SD" may be NE / not qualifying.
- **Up to the first PD only** — BOR is assessed until the first progression; you cannot get a better response back after that.
- **Once earned, a response is locked in** — because BOR takes the best so far, a **confirmed** CR/PR reached **before** the first PD makes the patient a **permanent responder**; later progression does **not** remove them from the ORR numerator (分子). The asymmetry (不对称): BOR only moves **up**, never down — a later PD just **ends the window**; it does not downgrade a response that was already reached. (The gate is **confirmation** — a single unconfirmed CR/PR does not count.)
- **NE** if there is no evaluable assessment after baseline.

Endpoints derived from BOR:

- **ORR (objective response rate, 客观缓解率)** = the proportion of patients whose BOR is CR or PR — see [[PSA (Prostate-Specific Antigen)|ORR / PSA50]] for the PSA-based version.
  - **Why ORR is built on BOR:** ORR asks a yes/no question for each patient — "did this tumour **ever** objectively shrink to PR/CR (up to progression)?" — and BOR is exactly the "best ever reached" status. A snapshot at a **fixed timepoint** would miss responders who responded **earlier** (and had already progressed by that visit) or **later** (not yet at that visit), because responses happen at different times and are **short-lived** (transient: shrink, then grow again). Taking the best over time captures "ever responded", whenever it happened. The built-in rules keep it honest — **confirmed** CR/PR, minimum SD duration, only up to the **first PD** — so "BOR = CR/PR" is a strict responder definition that does not depend on the visit schedule. (ORR tells you *whether*, not *how long* — how long it lasts is the separate **DoR**, duration of response.)
- **DCR (disease control rate, 疾病控制率)** = the proportion with a BOR of CR, PR **or SD** — it adds stable disease to ORR's CR/PR, i.e. "the disease **did not progress**". A **softer/weaker** signal than ORR, useful for **cytostatic** (细胞抑制性) drugs that stop growth rather than shrink the tumour. When SD must last a minimum time, it is often called **CBR** (clinical benefit rate, 临床获益率). SD is unclear without a control arm (it could be slow-growing, indolent 惰性, disease, not a drug effect), so DCR is read with caution.
- **DoR (duration of response, 缓解持续时间)** = among **responders only** (BOR CR/PR), the time from the **first documented CR/PR** to **progression or death** — how **long** the response lasts (durability, 持久性), summarized by the Kaplan–Meier median. It goes with ORR: **ORR = whether** it responded, **DoR = for how long**.

So the pipeline for each patient is: **timepoint statuses → BOR (best, with the confirmation/duration rules) → 1/0 responder flag → ORR across patients**.

These **response-based** endpoints (ORR, DCR, DoR) are different from the **time-to-event** ones — see [[Progression-Free Survival (PFS) and Overall Survival (OS)]] — and all are earlier [[Surrogate Endpoint|surrogates]] for **OS** (overall survival).
