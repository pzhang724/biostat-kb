From chat, 2026-06-11

Q: 不是分别列——我要 RECIST(软组织)和 PCWG3(骨)combine 到一起的单一判定方法/矩阵。

A:
Key asymmetry to state first: bone scan can only contribute PROGRESSION, not response. Bone-scan improvement is unreliable, so you cannot read CR/PR off bone. Therefore:
- RESPONSE (CR/PR/SD) is driven by the soft-tissue/nodal RECIST 1.1 call.
- PROGRESSION is a UNION (OR): soft-tissue RECIST PD OR bone 2+2 OR death.

Combined timepoint algorithm (one overall radiographic assessment):
1. Death? -> rPFS event.
2. Progression in EITHER compartment? soft-tissue RECIST = PD, OR bone meets confirmed 2+2 -> overall = PD (radiographic progression). Take the EARLIEST date; bone PD back-dated to first scan showing the initial 2 new lesions.
   - Bone caveat: >=2 new bone lesions seen but NOT yet confirmed by the next scan = NOT PD yet -> treat as non-PD pending confirmation; keep the soft-tissue category for now.
3. If no progression, assign the non-PD state from soft-tissue RECIST:
   - CR only if soft-tissue CR AND no bone lesions at all (none present, none new).
   - PR = soft-tissue PR (bone not progressing). [If soft-tissue is CR but bone lesions are present, you cannot call CR -> best is PR.]
   - SD / Non-CR-Non-PD = soft-tissue SD with bone not progressing.
   - NE if soft tissue not evaluable.

Combined matrix (rows = soft-tissue RECIST overall; cols = bone-scan 2+2 status):
| Soft tissue \ Bone | No new bone lesions      | >=2 new, UNconfirmed        | >=2 new, CONFIRMED (2+2) |
| CR                 | CR (if truly no bone)    | PR (await bone confirm)     | PD                       |
| PR                 | PR                       | PR (await bone confirm)     | PD                       |
| SD                 | SD                       | SD (await bone confirm)     | PD                       |
| PD (RECIST)        | PD                       | PD                          | PD                       |
| NE                 | NE                       | NE                          | PD                       |
- Any column "CONFIRMED 2+2" -> PD regardless of soft tissue.
- Any row "PD (RECIST)" -> PD regardless of bone.
- "UNconfirmed" bone column = not yet progression; carry the soft-tissue category until the confirmatory scan.
- Death anytime = rPFS event.

So the single rule: overall = PD if (soft-tissue PD) OR (bone 2+2 confirmed) OR death; otherwise overall = the soft-tissue RECIST category (with CR requiring zero bone disease). PSA and symptoms are NOT inputs to this radiographic call.
