From chat, 2026-06-20 (follow-up to BOIN)

Q: highlight 一下"照表执行，不实时建模"，最后用一个简单例子 illustrate

A:

Why "run it off a table, no live modeling":
- The two boundaries lambda_e, lambda_d are computed ONCE, before the trial, from the target
  DLT rate phi alone — they do NOT depend on accumulating data.
- From them you print a decision table indexed by "number of patients treated at the current
  dose": for each N it lists "escalate if #DLT <= a", "de-escalate if #DLT >= b", else stay.
- During conduct every decision = look up the row for the current dose's patient count, compare
  the DLT count, move. Arithmetic anyone can do — no statistician at the bedside, no software,
  no curve re-fitting after each cohort.
- Contrast CRM/EWOC: after EVERY cohort you must re-fit/update the dose-toxicity model with all
  data so far (software + statistician in the loop) to get the next dose. BOIN front-loads all
  the thinking into the table.
- The only modeling-like step in BOIN is a ONE-TIME isotonic regression at the very end to pick
  the MTD — not during escalation.

Pre-computed decision table (phi = 0.25):
  N at current dose:        3    6    9    12
  escalate if #DLT <=:      0    1    1    2
  de-escalate if #DLT >=:   1    2    3    4
  (otherwise stay)

Worked example (cohort size 3, doses D1<D2<D3, target 0.25):
  Cohort 1  D1  0 DLT  -> D1 0/3  -> table(3): 0<=0  escalate -> D2
  Cohort 2  D2  0 DLT  -> D2 0/3  -> table(3): 0<=0  escalate -> D3
  Cohort 3  D3  2 DLT  -> D3 2/3  -> table(3): 2>=1  de-escalate -> D2
  Cohort 4  D2  1 DLT  -> D2 1/6  -> table(6): 1<=1  escalate -> D3
  Cohort 5  D3  1 DLT  -> D3 3/6  -> table(6): 3>=2  de-escalate -> D2
  Cohort 6  D2  1 DLT  -> D2 2/9  -> table(9): =2    stay -> stop (max N reached)
Final tallies: D1 0/3 (0%), D2 2/9 (~22%), D3 3/6 (50%). MTD = the dose with rate closest to phi
and not over -> D2 (~22%, closest to 25%). Every step was a table lookup; the only computation
was the single end-of-trial MTD selection.
