From chat, 2026-06-22

Q: 嗯这个话题值得展开的详细一点 (expand estimand in more detail)

A (full expanded digest, page parity):

THE ESTIMATION CHAIN
- The estimand sits in a four-part chain that E9(R1) makes explicit:
  - Objective: the clinical question in words ("does drug A prolong survival vs B?").
  - Estimand: that question made precise via the five attributes — WHAT is being estimated.
  - Estimator: the statistical method used to estimate it (e.g. Cox model, MMRM).
  - Estimate: the actual number that comes out (e.g. HR = 0.72).
- Plus sensitivity analysis: separate analyses under DIFFERENT assumptions about the SAME estimand, to test robustness. (Distinct from a supplementary analysis, which targets a DIFFERENT estimand.)
- The key shift: pick the estimand FROM the clinical question, then choose the estimator to match — not "run the standard analysis and see what it estimates."

THE FIVE ATTRIBUTES (in detail)
1. Treatment — the treatment condition(s) compared: not just the drug, but dose, schedule, and what counts as the regimen (e.g. monotherapy vs add-on to standard of care). Defines both arms.
2. Population — the target patients the question is about, operationalized by inclusion/exclusion. Can be the whole trial population or a subgroup (a principal stratum is a special population defined by potential ICE behaviour).
3. Variable / endpoint — the outcome measured on each patient (e.g. OS, change-from-baseline FEV1). Includes how/when it's measured.
4. Intercurrent event (ICE) handling — for each ICE type, one of the five strategies below. THIS is the attribute E9(R1) added; it's where most of the thinking goes.
5. Population-level summary measure — how individual outcomes are condensed into one number comparing treatments: hazard ratio, difference in means, risk/odds ratio, etc.

THE FIVE ICE HANDLING STRATEGIES (what each does + when used)
- Treatment policy: use the observed outcome regardless of the ICE — the ICE is part of the treatment "policy". Effect = effect of being assigned the regimen, whatever happens after. ITT spirit. Used for OS (you keep following the patient even after they switch/stop). Cannot apply to an endpoint that stops existing after the ICE (e.g. can't measure on-treatment tumour size after death).
- Hypothetical: the value that WOULD have been observed had the ICE not happened. Used when you want the effect in a world without the complication — e.g. censor OS at the time a patient starts subsequent anti-cancer therapy, asking "effect if no one switched."
- Composite: fold the ICE INTO the endpoint definition, treating its occurrence as part of the outcome (often as failure). Used when the ICE itself is a bad outcome — e.g. "treatment failure" = progression OR rescue-medication use OR discontinuation for toxicity.
- While on treatment: use only the outcome up to the ICE — the effect during the time the patient is actually on treatment. Used e.g. for symptom/PRO endpoints where only the on-treatment experience is of interest.
- Principal stratum: restrict to the subpopulation that would NOT experience the ICE (under either treatment). Used e.g. for the effect among patients who would adhere, or who would never need rescue. Hard to identify in practice (the stratum membership is partly unobserved).

WHY IT CHANGED PRACTICE
- Before E9(R1), the analysis hid the real target: "ITT vs per-protocol", how dropouts were imputed, how switches/rescue meds were handled — all buried in the SAP, often inconsistent, decided after the fact.
- The estimand framework forces these choices UP FRONT and INTO the objective: you state the clinical question precisely, including how complications are handled, before choosing a method. Same data + different ICE strategy = genuinely different question, not just a different analysis.

WORKED ONCOLOGY EXAMPLE (one endpoint, two estimands)
- Endpoint: OS. ICE of interest: subsequent anti-cancer therapy (patients on control often switch to effective drugs after progression).
- Estimand A (treatment-policy): keep following OS no matter what they take next. Answers "real-world effect of starting on this drug." Switching dilutes the control arm's apparent disadvantage → effect looks smaller.
- Estimand B (hypothetical): censor OS at the switch. Answers "effect if no one had switched" — closer to the drug's intrinsic effect, but relies on censoring assumptions.
- Same patients, same OS data, two different numbers — because the ICE attribute differs. That is the whole point of specifying the estimand.
