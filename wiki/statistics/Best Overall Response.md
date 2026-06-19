---
title: "Best Overall Response"
type: concept
status: learned
tags: [statistics, medical]
created: 2026-06-11
updated: 2026-06-19
sources: 2
---

# Best Overall Response

The key framing: **however complex the criterion is, at a single timepoint a patient has exactly ONE response status — and the "best" is the best among all those timepoint statuses.** This is the two-level structure behind response endpoints.

- **Timepoint (visit) response** — at each assessment the criterion (e.g. [[Modified RECIST 1.1 and PCWG3 Criteria]], or plain [[RECIST 1.1]]) collapses everything — target, non-target, new lesions, bone — into **one** status: **CR / PR / SD / PD / NE**.
- **Best Overall Response (BOR, 最佳总体缓解)** — the single **best** status recorded across **all** timepoints from baseline until progression/death/end of follow-up. Ordering **CR > PR > SD > PD** (NE handled separately). "Best is among all these" = take the max over the visit sequence.

## Ordering, best → worst

By tumour burden / favorability:

> **CR ≈ NED  >  PR  >  SD  >  PD**  — and **NE sits outside the ordering**.

- **CR** (Complete Response 完全缓解) — all known disease gone (best).
- **NED** (No Evidence of Disease 无疾病证据) — no detectable disease; ranks **alongside CR**. But it's a **clinical / post-surgical** term (patient rendered disease-free after resection, or entered with no measurable disease), **not** a standard [[RECIST 1.1]] timepoint category — RECIST uses **CR**. It surfaces in CDISC response controlled terminology / adjuvant settings.
- **PR** (Partial Response 部分缓解) — substantial shrinkage (≥30% in SoD).
- **SD** (Stable Disease 疾病稳定) — neither PR nor PD.
- **PD** (Progressive Disease 疾病进展) — growth / new lesions (worst).
- **NE** (Not Evaluable 不可评估) — assessment couldn't be made (missing/inadequate). **Not** better or worse — it's "unknown", so it is **off** the favorability scale (handled separately below).

Rules that constrain the max:

- **Confirmation** — in ORR-primary / non-randomized trials a CR or PR must be **confirmed** by a repeat assessment ≥4 weeks later, or it doesn't count as BOR.
- **Minimum SD duration** — SD only qualifies after a protocol-defined minimum interval from baseline (e.g. ≥6–8 weeks); an earlier "SD" may be NE/non-qualifying.
- **Up to first PD only** — BOR is assessed until the first progression; you cannot recover a better response afterward.
- **NE** if there is no evaluable post-baseline assessment.

Downstream endpoints derive from BOR:

- **ORR (objective response rate)** = proportion of patients whose BOR is CR or PR — see [[PSA (Prostate-Specific Antigen)|ORR / PSA50]] for the PSA-based analogue.
- **DCR (disease control rate)** = proportion with BOR of CR, PR, or SD.

So the per-patient pipeline is: **timepoint statuses → BOR (best, with confirmation/duration rules) → 1/0 responder flag → ORR across patients**.

