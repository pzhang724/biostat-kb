From chat, 2026-06-22

Q: 这些 strategy 解释起来很拗口，有没有通俗易懂的讲法？通常什么情况下用？数学公式在做什么假设？

A (plain-language rewrite of the five ICE strategies, with typical use + the underlying math assumption):

Anchor with ONE patient: a control-arm patient who, after progression, switches to another cancer drug (a classic ICE), then later dies. Their OS is "polluted" by the switch. Each strategy = a different answer to "what do we do with this patient?":

- Treatment policy — Plain: keep their real death time, ignore that they switched (count everything as-is). Typically used for: hard regulatory endpoints like OS where what happens after is part of reality — the default ITT-style primary analysis. Math assumption: almost none beyond standard randomization + administrative censoring; you analyze observed data as-is. Robust, but the effect is "diluted" by post-ICE behaviour.
- Hypothetical — Plain: pretend the switch never happened — censor at the switch and statistically reconstruct "what would their OS have been if they'd never switched." Typically used for: stripping out an ICE you don't want to credit/blame on the study drug (rescue meds, subsequent therapy). Math assumption: censoring at the ICE is non-informative / MAR — the censored patient's future would look like comparable patients still at risk. Untestable — the load-bearing assumption.
- Composite — Plain: count the switch ITSELF as an event/failure (fold it into the endpoint). Typically used for: when the ICE is itself a bad outcome (discontinuation for toxicity, needing rescue medication). Math assumption: little statistical assumption — nothing goes missing (the ICE is observed); the real "assumption" is the clinical judgment that the ICE deserves to count as failure.
- While on treatment — Plain: only use the outcome up to the switch, ignore everything after. Typically used for: symptom / PRO / QoL endpoints where only the on-treatment experience matters. Math assumption: that the (patient-varying) on-treatment window IS the intended quantity — different patients contribute different durations by design, not as bias.
- Principal stratum — Plain: only analyze the patients who wouldn't have switched at all (under either arm). Typically used for: effect among adherers/tolerators, complier effects, vaccine efficacy among the would-be-infected. Math assumption: the latent stratum is only partly observed (you see one arm per patient), so it needs strong identifying assumptions (monotonicity / exclusion-restriction, CACE/IV-style). Most assumption-heavy; often only bounds.

Takeaway — assumption burden rises: treatment-policy (lightest) → composite / while-on-treatment (modest) → hypothetical (strong, untestable MAR) → principal stratum (strongest, partly unidentified).
