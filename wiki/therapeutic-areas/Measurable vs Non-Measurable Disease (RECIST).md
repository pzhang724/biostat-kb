---
title: "Measurable vs Non-Measurable Disease (RECIST)"
type: concept
status: learned
tags: [medical, statistics]
created: 2026-06-11
updated: 2026-06-11
sources: 1
---

# Measurable vs Non-Measurable Disease (RECIST)

A few linked terms used in solid-tumor response assessment:

- **Lesion vs tumor (病灶 vs 肿瘤)** — not identical. A **lesion (病灶)** is *any* localized area of abnormal/diseased tissue (could be a tumor, but also inflammation, a cyst, a scar); a **tumor (肿瘤)** is specifically an abnormal mass of proliferating tissue. So lesion ⊃ tumor — every tumor is a lesion, not vice versa. RECIST says "lesion" (not "tumor") on purpose, since some target lesions are e.g. lymph nodes. In a cancer trial the tracked lesions *are* tumors, so colloquially 病灶 ≈ 肿瘤 there.
- **Lesion (病灶)** — a discrete site of diseased tissue; in oncology, a tumor site. A patient typically has several: the primary tumor plus metastases. The specific lesions chosen to measure and follow over time are **target lesions**. (灶 = hearth/stove; 病灶 = the "hearth" of disease, its focal central point — the same hearth metaphor as the Latin *focus* = fireplace that "focus of disease" comes from.)
- **Primary vs metastatic (原发灶 vs 转移灶)** — the **primary tumor (原发灶)** is where the cancer *started* (the prostate, in prostate cancer); a **metastatic lesion (转移灶)** is a *new, secondary* site the cancer spread **to**, not the origin. 转移 = "transfer/move", so 转移灶 is the moved-to destination. A patient's "multiple lesions" = the primary plus its metastases.
- **Bone metastasis (骨转移)** — cancer that has spread from the primary organ to bone (very common in prostate and breast cancer). Seen on bone scan / CT / MRI as areas of abnormal bone.

**Measurable vs non-measurable** is a **[[RECIST 1.1]]** distinction:

- **Measurable** — a lesion with a clean, reproducibly measurable diameter: ≥10 mm longest diameter on CT for soft-tissue lesions (≥15 mm short axis for lymph nodes). Because you can track it in mm, it can drive CR / PR / PD response calls.
- **Non-measurable** — lesions too small (<10 mm) or without a measurable border, plus whole categories that are non-measurable *by definition*: **bone metastases** (lytic/blastic disease has no soft-tissue diameter), leptomeningeal disease, ascites, pleural/pericardial effusions, lymphangitic spread.

**A patient usually has many lesions, not one tumor** (原发肿瘤 + 多处转移). RECIST picks a limited set of measurable lesions as **target lesions**, measures each, and tracks the **sum of diameters (SoD)** over time; the rest are **non-target** lesions assessed qualitatively. Response (CR/PR/SD/PD) is judged on the **aggregate burden**, not a single lesion — so "the tumor shrank" means total burden fell. Because lesions can behave heterogeneously (some shrink while others grow), any single aggregate (SoD, or a systemic marker like PSA) can mask a **mixed response**.

Why it matters statistically: RECIST-based [[PSA (Prostate-Specific Antigen)|ORR]] requires **measurable disease at baseline**. Bone-predominant patients — typical in prostate cancer — often have no measurable target lesion, so RECIST ORR is not evaluable for them. That is precisely why **PSA-based response (PSA50)** and bone-scan progression criteria ([[PCWG3 Criteria]]) are used instead. See [[PSA (Prostate-Specific Antigen)]].

