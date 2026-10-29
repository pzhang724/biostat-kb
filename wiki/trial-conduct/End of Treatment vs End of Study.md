---
title: "End of Treatment vs End of Study"
type: concept
status: learned
created: 2026-06-18
---

# End of Treatment vs End of Study

Two different milestones (里程碑) in a subject's participation in a trial.

- **End of Treatment (EOT, 治疗结束)** — the point when a patient **stops the study drug** (试验药物): they finished the planned cycles, or had disease **progression** (进展), unacceptable **toxicity** (毒性), withdrew consent, died, etc. It triggers an **EOT visit** + an EOT disposition record (处置记录).
- **End of Study (EOS, 研究结束)** — the point when a patient's **whole participation** ends: the **last contact / last data point**, after any follow-up that continues after treatment. It triggers an **EOS visit** + an EOS disposition record.

**The difference in one line: EOT = stop the *drug*; EOS = stop *everything* (last contact).** A patient is often **off treatment but still on study**, in the follow-up period between EOT and EOS.

## Between EOT and EOS

- **Safety follow-up** (安全随访, ~30 days after the last dose) — collect AEs/SAEs and subsequent therapy.
- **Long-term / survival follow-up** (生存随访) — survival status + subsequent anti-cancer therapy, which feed OS (overall survival).

## Two senses of "End of Study"

- **(a) Subject level** — one person's end of participation.
- **(b) Trial level** — the end of the whole study = **Last Subject Last Visit (LSLV, 末例受试者末次访视)** → **database lock** (数据库锁定). The context tells you which one is meant.

## Why a biostatistician cares

OS is measured from randomization to death, **censored** (删失) at the EOS / last-known-alive date — so the EOT→EOS follow-up window is exactly what feeds the survival endpoints. The **DS (Disposition)** domain records **both** the EOT reason and the EOS reason. Going off treatment is an [[Intercurrent Event]] that is handled differently across estimands (treatment-policy vs hypothetical).

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

A trial-conduct concept that feeds survival analysis in [[Oncology]]; the visit/period structure is laid out in the [[Schedule of Assessments]].
