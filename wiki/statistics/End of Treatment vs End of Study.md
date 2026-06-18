---
title: "End of Treatment vs End of Study"
type: concept
status: learned
tags: [trial-conduct, statistics, medical]
created: 2026-06-18
updated: 2026-06-18
sources: 1
---

# End of Treatment vs End of Study

Two distinct milestones in a subject's trial participation.

- **End of Treatment (EOT, 治疗结束)** — the point a patient **stops the study drug** (投资药物): completed planned cycles, disease **progression** (进展), unacceptable **toxicity** (毒性), withdrawal of consent, death, etc. Triggers an **EOT visit** + an EOT disposition record.
- **End of Study (EOS, 研究结束)** — the point a patient's **entire participation** ends: the **last contact / last data point**, after any follow-up that continues post-treatment. Triggers an **EOS visit** + EOS disposition record.

**The difference in one line: EOT = stop the *drug*; EOS = stop *everything* (last contact).** A patient is commonly **off-treatment but still on-study**, sitting in the follow-up period between EOT and EOS.

## Between EOT and EOS

- **Safety follow-up** (安全随访, ~30 days after last dose) — collect AEs/SAEs, subsequent therapy.
- **Long-term / survival follow-up** (生存随访) — survival status + subsequent anti-cancer therapy, feeding OS.

## Two senses of "End of Study"

- **(a) Subject level** — an individual's end of participation.
- **(b) Trial level** — the whole study's end = **Last Subject Last Visit (LSLV)** → **database lock** (数据库锁定). Context tells which.

## Why a biostatistician cares

OS is measured from randomization to death, **censored** (删失) at the EOS / last-known-alive date — so the EOT→EOS follow-up window is exactly what feeds survival endpoints. The **DS (Disposition)** domain records **both** the EOT reason and the EOS reason. Going off treatment is an [[Intercurrent Event]] handled differently across estimands (treatment-policy vs hypothetical).

## Timeline

```
Screening
   │
   ▼
Treatment period (cycles / dosing)
   │
   ▼  ◀── EOT: stop study drug (progression / toxicity / completed / withdrawal)
Safety follow-up (~30 days post last dose: AEs, subsequent therapy)
   │
   ▼
Long-term / survival follow-up (survival status, subsequent anti-cancer therapy)
   │
   ▼  ◀── EOS: last visit / last contact = end of participation
(study-level: when the LAST subject reaches EOS = LSLV → database lock)

On-treatment │←—— EOT ——→│ off-treatment but still ON-STUDY │←—— EOS ——→│ off-study
```

A trial-conduct concept feeding survival analysis in [[Oncology]].
