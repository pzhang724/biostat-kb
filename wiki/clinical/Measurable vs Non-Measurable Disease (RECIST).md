---
title: "Measurable vs Non-Measurable Disease (RECIST)"
type: concept
status: learned
created: 2026-06-11
---

# Measurable vs Non-Measurable Disease (RECIST)

A few linked terms used in response assessment of solid tumors (实体瘤):

- **Lesion vs tumor (病灶 vs 肿瘤)** — not the same. A **lesion (病灶)** is *any* local area of abnormal/diseased tissue (it could be a tumor, but also inflammation, a cyst 囊肿, a scar 瘢痕). A **tumor (肿瘤)** is specifically an abnormal mass (肿块) of growing (proliferating, 增殖) tissue. So lesion ⊃ tumor — every tumor is a lesion, but not every lesion is a tumor. RECIST says "lesion" (not "tumor") on purpose, because some target lesions are e.g. lymph nodes. In a cancer trial the tracked lesions *are* tumors, so in everyday speech (colloquially, 口语中) 病灶 ≈ 肿瘤 there.
- **Lesion (病灶)** — a separate (discrete) site of diseased tissue; in oncology, a tumor site. A patient usually has several: the primary tumor plus metastases (转移灶). The specific lesions chosen to measure and follow over time are **target lesions** (靶病灶). (灶 = hearth/stove 灶台; 病灶 = the "hearth" of the disease, its central focal point — the same hearth image as the Latin *focus* = fireplace, where "focus of disease" comes from.)
- **Primary vs metastatic (原发灶 vs 转移灶)** — the **primary tumor (原发灶)** is where the cancer *started* (the prostate, in prostate cancer). A **metastatic lesion (转移灶)** is a *new, secondary* site the cancer spread **to**, not the origin. 转移 = "transfer/move", so 转移灶 is the place it moved to. A patient's "multiple lesions" = the primary plus its metastases.
- **Bone metastasis (骨转移)** — cancer that has spread from the primary organ to bone (very common in prostate and breast cancer). Seen on bone scan (骨扫描) / CT / MRI as areas of abnormal bone.

**Measurable vs non-measurable** is a **[[RECIST 1.1]]** distinction:

- **Measurable** (可测量) — a lesion with a clear diameter that can be measured the same way each time (reproducibly): ≥10 mm longest diameter on CT for soft-tissue lesions (≥15 mm short axis 短径 for lymph nodes). Because you can track it in mm, it can drive CR / PR / PD response calls (complete response 完全缓解 / partial response 部分缓解 / progressive disease 疾病进展).
- **Non-measurable** (不可测量) — lesions that are too small (<10 mm) or have no measurable border, plus whole groups that are non-measurable *by definition*: **bone metastases** (lytic 溶骨性 / blastic 成骨性 disease has no soft-tissue diameter), leptomeningeal disease (软脑膜病变), ascites (腹水), pleural/pericardial effusions (胸腔/心包积液), lymphangitic spread (癌性淋巴管炎).

**A patient usually has many lesions, not one tumor** (原发肿瘤 + 多处转移). RECIST picks a limited set of measurable lesions as **target lesions**, measures each, and tracks the **sum of diameters (SoD, 直径总和)** over time; the rest are **non-target** lesions, assessed qualitatively (定性地). Response (CR/PR/SD/PD; SD = stable disease, 疾病稳定) is judged on the **total burden** (aggregate, 总负荷), not on a single lesion — so "the tumor shrank" means the total burden fell. Because lesions can behave differently (heterogeneously, 异质性地 — some shrink while others grow), any single total (SoD, or a whole-body marker like PSA) can hide a **mixed response** (混合缓解).

Why it matters for statistics: RECIST-based [[PSA (Prostate-Specific Antigen)|ORR]] (objective response rate, 客观缓解率) requires **measurable disease at baseline**. Patients with mainly bone disease (bone-predominant) — typical in prostate cancer — often have no measurable target lesion, so RECIST ORR cannot be evaluated for them. That is exactly why **PSA-based response (PSA50)** and bone-scan progression criteria ([[PCWG3 Criteria]]) are used instead. See [[PSA (Prostate-Specific Antigen)]].
