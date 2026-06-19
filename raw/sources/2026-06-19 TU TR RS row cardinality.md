From chat, 2026-06-19 (follow-up)

User's model of row counts per patient:
- TU: multiple lesions x their info x number of evaluators.
- TR: same number of observations as TU, recording length/state, also by evaluator.
- RS: based on the criteria, maybe only 1 to 3, depending on number of evaluators.

Correction / precise cardinality per patient:

- TU ~ #lesions x #evaluators. One row per lesion per evaluator (identity, set when the lesion is first identified; new lesions appended later). User is right here.

- TR ~ #lesions x #VISITS x #evaluators. One row per lesion PER VISIT per evaluator (measurements repeat at every visit). So "same number as TU" is true ONLY per-visit — at one visit TR's lesion rows ~ TU's lesion count. But the TOTAL TR is much bigger than TU, multiplied by the number of visits. TR is the largest of the three.

- RS ~ #response-params x #VISITS x #evaluators (+ a BOR record). It's NOT just 1-3 total. Per visit per evaluator you get the overall response (and often separate target / non-target / new-lesion / overall rows), and that repeats EVERY visit. The "1 to 3" the user sensed is closer to the number of evaluators per visit, not the total.

Evaluators multiplier: investigator (1) + central reader 1 + reader 2 + adjudicator-when-discordant -> roughly x1 to x4.

Key fix: TU is set once per lesion (identity); TR and RS REPEAT per visit. So TR total = TU-lesion-count x visits, and RS total = visits x evaluators (x response params), not a small fixed number.
