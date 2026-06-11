From chat, 2026-06-11

Q: 能把所有的 combination 的决定列出来吗?(list all the combination -> overall-assessment decisions)

A:

RECIST 1.1 — time-point overall response, patients WITH target lesions
(combination of Target × Non-target × New lesions -> Overall)
| Target            | Non-target              | New lesions | Overall |
| CR                | CR                      | No          | CR      |
| CR                | Non-CR/Non-PD           | No          | PR      |
| CR                | NE (not all evaluated)  | No          | PR      |
| PR                | Non-PD or NE            | No          | PR      |
| SD                | Non-PD or NE            | No          | SD      |
| NE (not all eval) | Non-PD                  | No          | NE      |
| PD                | Any                     | Yes or No   | PD      |
| Any               | PD                      | Yes or No   | PD      |
| Any               | Any                     | Yes         | PD      |
- i.e. progression in ANY of {target, non-target, new lesion} => overall PD.
- CR requires CR in both target and non-target and no new lesions.

RECIST 1.1 — patients with NON-TARGET disease ONLY (no measurable target)
| Non-target          | New lesions | Overall            |
| CR                  | No          | CR                 |
| Non-CR/Non-PD       | No          | Non-CR/Non-PD      |
| NE                  | No          | NE                 |
| Unequivocal PD      | Yes or No   | PD                 |
| Any                 | Yes         | PD                 |
- Note: "Non-CR/Non-PD" is used instead of "SD" when there are no measurable target lesions.

PCWG3 — combining compartments into radiographic progression / rPFS
- Soft tissue/nodes: RECIST 1.1 PD (as above).
- Bone: 2+2 rule on bone scan.
- rPFS event = EARLIEST of { soft-tissue PD (RECIST) OR bone PD (2+2) OR death }. OR logic — any one triggers it.
- Bone progression date = back-dated to first scan showing the initial 2 new lesions.
- PSA progression (>=25% & >=2 ng/mL above nadir, confirmed) and symptomatic progression are SEPARATE endpoints, not part of the radiographic call; no PD on PSA alone.

Definitions reminder:
- CR complete response, PR partial response, SD stable disease, PD progressive disease, NE not evaluable.
