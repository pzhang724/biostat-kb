---
title: "Anti-Cancer Therapy Categories in Oncology Trials"
type: concept
status: learned
tags: [trial-conduct, data-management]
created: 2026-06-11
updated: 2026-06-11
sources: 2
---

# Anti-Cancer Therapy Categories in Oncology Trials

In an oncology trial, cancer-directed treatments are sorted into non-overlapping buckets by their **role relative to the study drug**. The study drug is the studied "independent variable"; every other anti-cancer therapy is a confounder to control or explain.

Pharmacologically, the study drug *is* a type of anti-cancer therapy — the buckets below are a **trial-data distinction**, not a biological one.

- **Study drug / Investigational Product (IP)** — the single product being evaluated for safety/efficacy. SDTM **EX** (EC if needed).
- **Prior anti-cancer therapy** — treatments before enrollment. Drives eligibility, washout, line of therapy, refractory status. SDTM **CM** (drugs) / **PR** (radiation, surgery).
- **Concomitant anti-cancer therapy** — usually *prohibited* during study; if it occurs it contaminates efficacy/safety attribution (often a protocol deviation).
- **Subsequent anti-cancer therapy** — taken after discontinuation; a major **OS** confounder (crossover, later lines) and the most common [[Intercurrent Event]] in OS analysis.

A bare "anti-cancer therapy used = Yes" flag means little on its own — the load-bearing question is *when* and *at what stage relative to the study drug*, which assigns it to one of the buckets above and decides whether it is a baseline characteristic, a covariate/confounder, or a signal to explain.

Why it matters for analysis: AE attribution (study drug vs concomitant), efficacy purity ([[PSA (Prostate-Specific Antigen)|PSA]]/RECIST/PET), OS interpretation (subsequent therapy), and baseline characterization (prior therapy defines line & refractory status).

