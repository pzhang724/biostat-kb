From chat, 2026-06-11

Human's point: no matter how complex the criterion is, at a single timepoint a patient has exactly ONE response status; the "best" is the best among all those timepoint statuses.

Confirmation / answer — this is exactly the two-level structure:
- Level 1 — TIMEPOINT (visit) response: at each assessment the criterion (e.g. modified RECIST 1.1 + PCWG3 fused matrix) yields ONE status: CR / PR / SD / PD / NE. One status per timepoint, full stop.
- Level 2 — BEST OVERALL RESPONSE (BOR): the single best status recorded across ALL timepoints from baseline until progression/death/end of follow-up. Ordering: CR > PR > SD > PD (NE handled separately). "Best is among all these" = take the max over the timepoint sequence.

Rules that constrain the "max":
- Confirmation: in ORR-primary / non-randomized trials, a CR or PR must be CONFIRMED by a repeat assessment >=4 weeks later, otherwise it doesn't count as the BOR.
- SD requires a MINIMUM duration (a protocol-defined minimum interval from baseline, e.g. >=6-8 weeks); an early SD before that window may be NE/not-qualifying.
- BOR is assessed only up to first PD — you can't "recover" a better response after progression.
- NE if no evaluable post-baseline assessment.

Downstream:
- ORR (objective response rate) = proportion of patients whose BOR is CR or PR.
- DCR (disease control rate) = proportion with BOR of CR, PR, or SD.
- So the per-patient pipeline is: timepoint statuses -> BOR (best, with confirmation/duration rules) -> 1/0 responder flag -> ORR across patients.
