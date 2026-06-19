From chat, 2026-06-19 (follow-up, confirmation)

User restated: "So first select the location -> recorded in TU; then measure -> recorded in TR; then see if it's a response -> that calculation in RS."

A: Right, that's the pipeline. Two refinements:
- TU is not just "location" — its key job is to IDENTIFY + CLASSIFY each lesion (location TULOC + the classification TUSTRESC = TARGET / NON-TARGET / NEW). The target-vs-non-target call is the load-bearing part, because it determines how TR measures it and how RS integrates it.
- RS is where the response VERDICT lives (overall response). The actual RECIST math (sum of diameters, % change vs baseline/nadir) is the derivation that produces it — in ADaM that's ADTR (sum) -> ADRS (response). RS itself can be either COLLECTED (investigator/BICR provides the response) or DERIVED by the programmer, per the SAP.

So: TU = identify + classify (which lesion, what type); TR = measure (how big / state); RS = response verdict (computed/integrated from TR + non-target + new lesions).
