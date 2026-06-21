From chat, 2026-06-20

Q: 讲一下 Simon 2-stage minimax

A: Simon's two-stage design is a phase II, single-arm design for a binary endpoint
(response / no response, e.g. ORR) to screen whether a new agent is active enough to pursue.
It has a built-in interim futility stop so an inactive drug can be abandoned early.

Hypotheses: p0 = response rate not worth pursuing (uninteresting), p1 = target rate of interest.
Test H0: p <= p0 vs p >= p1, controlling type I error alpha and power 1-beta at p1.

Mechanics (parameters n1, r1, n, r):
- Stage 1: treat n1 patients. If responses <= r1 -> STOP for futility (drug not promising).
  Otherwise continue.
- Stage 2: treat up to total n (= n1 + n2). If total responses <= r -> not promising;
  if > r -> promising (worth further development).
- Early stopping is ONLY for futility (ethical: limit patients exposed to an inactive drug);
  there is no early stop for efficacy.

Two standard choices among all (n1,r1,n,r) that meet the alpha and power constraints:
- Optimal: minimizes the EXPECTED sample size under the null, EN(p0) -> stops early most often
  when the drug doesn't work.
- Minimax: minimizes the MAXIMUM (total) sample size n -> smallest worst-case n.

Minimax highlight: pick it when accrual is slow / patients are scarce or expensive and you want
the smallest possible total n. Trade-off: minimax usually has a larger n1 and a larger EN(p0)
(stops early less often) than the optimal design; optimal has a smaller EN(p0) but a larger
maximum n. ("Admissible" designs compromise between the two.)

Worked example (computed; p0=0.10, p1=0.30, alpha=0.05, power=0.80):
- Optimal: stage1 1/10 (stop if <=1 response in 10), total 5/29 (active if >5 in 29);
  EN(p0)=15.0, P(stop early|p0)=74%.
- Minimax: stage1 1/15, total 5/25; EN(p0)=19.5, P(stop early|p0)=55%.
Minimax total n=25 < optimal's 29 (smaller worst case), but minimax expects MORE patients under
the null (19.5 vs 15.0) because it stops early less often.
