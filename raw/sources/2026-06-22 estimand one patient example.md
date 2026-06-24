From chat, 2026-06-22

Q: 能拿一个 patient 真实的 data 来举例吗？

A: Used a realistic SYNTHETIC single patient (not real PHI — real patient-level data can't go in the repo, and none was supplied). One mCRPC control-arm patient, OS endpoint, with a switch ICE. Shows how each of the five strategies records THIS patient's OS row differently.

Timeline (illustrative, synthetic — Patient "07", control arm, mCRPC):
- Day 0   — randomized to control arm, starts treatment
- Day 185 — radiographic progression (PD); discontinues study treatment
- Day 210 — starts subsequent anti-cancer therapy (the SWITCH = the intercurrent event)
- Day 540 — dies
- Day 600 — database cutoff

OS endpoint = time from randomization to death. How each strategy records this patient's (time, status):

- Treatment policy: death counts as-is, switch ignored → time = 540, status = EVENT (death). The "whatever happens after" is included.
- Hypothetical (censor at the switch): pretend no switch → time = 210, status = CENSORED at the switch; the post-210 "no-switch" survival is reconstructed statistically from comparable still-at-risk patients.
- Composite (endpoint = death OR switch, whichever first): the switch is itself the failure → time = 210, status = EVENT (failure). Dies-later is irrelevant; the switch already "counts."
- While on treatment: the death happened OFF treatment (discontinued day 185) → time = 185, status = CENSORED at discontinuation. The off-treatment death doesn't count. (Somewhat artificial for OS — while-on-treatment fits symptom/PRO endpoints better — but shows the mechanic.)
- Principal stratum (restrict to "would-not-switch"): this patient DID switch → they are NOT in that stratum → EXCLUDED from the analysis set entirely (no row).

Punchline: ONE patient, but the analysis "sees" 540-event / 210-censored / 210-event / 185-censored / nothing-at-all depending on the strategy. Five different inputs → this single patient pushes five different effect estimates in five different directions. That is why the estimand (specifically the ICE attribute) has to be fixed before any analysis.
