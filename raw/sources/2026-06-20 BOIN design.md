From chat, 2026-06-20

Q: 给我解释一下 BOIN design

A: BOIN = Bayesian Optimal Interval design — a phase I dose-finding (dose-escalation) design
used to find the MTD, in the "model-assisted" family that sits between algorithm-based designs
(3+3) and fully model-based designs (CRM, EWOC).

Core rule (up-and-down by an interval): pre-specify a target DLT rate phi (e.g. 0.25). From phi
two fixed boundaries are derived, lambda_e (escalation) and lambda_d (de-escalation), e.g. for
phi=0.25 about 0.197 and 0.298. At the current dose compute the observed DLT rate p_hat =
#DLTs / #patients, then:
  - p_hat <= lambda_e  -> escalate to next higher dose
  - p_hat >= lambda_d  -> de-escalate
  - in between          -> stay at the current dose
Plus a safety rule to eliminate overly toxic doses. The boundaries are "optimal" because they
are derived to minimize the probability of incorrect escalation/de-escalation decisions.

Why it is attractive: it combines the simplicity/transparency of algorithm-based designs
(decisions can be pre-tabulated into a chart the team follows, no real-time modeling or software
during conduct) with operating characteristics comparable to CRM. Decision depends only on the
current dose's data, target phi, and the fixed boundaries.

vs 3+3: BOIN targets a specified DLT rate, allows any cohort size, and has better operating
characteristics. vs CRM/EWOC: CRM/EWOC fit/update a dose-toxicity curve continuously
(model-based); BOIN is model-ASSISTED — a likelihood/Bayesian justification produces the
boundaries, but the actual trial rule is a simple interval comparison, no curve fitting.

MTD selection at the end: after the trial stops (max sample size reached, etc.), estimate the
toxicity rates by isotonic regression and pick the dose with rate closest to phi.

Extensions: TITE-BOIN (time-to-event, handles late-onset toxicity — relevant to long/delayed
toxicities like radioligands); BOIN12 (utility-based, jointly uses toxicity + efficacy for dose
OPTIMIZATION, Project Optimus relevant); combination/drug-combo BOIN.
