From chat, 2026-06-11

Q: Intercurrent event 呢?(follow-up after anti-cancer therapy categories)

A:
- Intercurrent event (ICE, 伴发/中间事件): an ICH E9(R1) estimand-framework concept — an event occurring AFTER treatment initiation that affects either the interpretation or the existence of the outcome measurement.
- Examples: discontinuation / switching treatment, use of prohibited/rescue concomitant medication, subsequent anti-cancer therapy, death (for non-survival endpoints).
- Distinct from a plain covariate or from missing data: after an ICE the quantity you intended to measure changes meaning.
- ICH E9(R1) requires pre-specifying, per ICE type, one of five handling STRATEGIES:
  - Treatment policy: ignore the ICE, use observed value regardless (ITT spirit).
  - Hypothetical: envisage the outcome had the ICE not occurred.
  - Composite: fold the ICE into the endpoint definition (e.g. count as failure).
  - While on treatment: use only the outcome up to the ICE.
  - Principal stratum: estimate within the subpopulation that would not experience the ICE.
- Connection: subsequent anti-cancer therapy is the most common ICE in OS analysis — treatment-policy keeps following OS as usual; hypothetical censors at switch.
