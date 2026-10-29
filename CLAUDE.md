# CLAUDE.md — biostat-kb Operating Schema

`biostat-kb` is a personal **learning ledger** for a clinical-trial biostatistician. You (Claude) maintain `wiki/`. The human supplies material and directs what to ingest. In `raw/` you only ever **create** capture files — never modify or delete a human-authored one.

## Purpose — read this first

This wiki is **NOT an encyclopedia**. It lets the human:

1. **Confirm what they have learned** — a page existing means "I learned this";
2. **See what they have not learned yet** — to-learn checklists;
3. **Navigate connections** between learned items — wiki-links, rendered by Quartz as backlinks and a graph. This is the main value; keep the links rich.

So:

- **Be terse.** A page is a definition, a handful of key points, and links — a marker that learning happened, never textbook prose or a substitute for the source.
- **Never fabricate coverage.** Only write pages for material the human actually ingested or said they learned.
- **A page must not exceed what the human saw.** The ceiling is what you told the human in chat. Do not add facts, parameters, caveats, examples or references that weren't in the conversation, even if correct. When unsure whether something was said, leave it out.

## Sources

Material enters in exactly three forms; each is captured to `raw/` first, then ingested:

1. **A link** — fetch it, save a copy to `raw/sources/`.
2. **An uploaded file / picture** — save to `raw/sources/` (notes/docs) or `raw/assets/` (images/PDFs).
3. **Knowledge shared in chat** — capture the human's own words, not your elaboration.

- File name: `raw/sources/YYYY-MM-DD <short topic>.md`; first line gives the origin (`Source: <url>, captured <date>` · `Uploaded file, <date>` · `From chat, <date>`).
- Your own explanations are not a source — except via the Q&A preference below.
- Distinguish material from commands: "ingest X", "lint", "what next", "restructure this" are instructions to execute, not material to save. If a chat remark (not a question) might be either material or just conversation, ask before capturing.
- `raw/` is provenance only and is **not published**. There is no per-source page in `wiki/`; the content page plus its `log.md` line is the published record.

## User Preferences

Durable preferences live here (the repo travels between machines). Add new ones to this section.

- **Save Q&A by default — never ask whether to.** Every substantive question the human asks (follow-ups and clarifications included) plus your answer is material: capture it as `From chat` and run a light-touch ingest without asking. Pure commands are still just commands.
- **Answer short first.** A short paragraph (~4–6 sentences or a few bullets): direct answer plus a little context. The human follows up for detail.
- **Record first, answer last.** Do the capture/ingest/sync before giving the answer, so the answer is the last thing in the turn. A one-line note like "记录并 ingest" before the tool calls is fine.
- **Gloss terms in Chinese, not sentences.** Add a Chinese gloss after each load-bearing **term** (e.g. `lesion (病灶)`, `dose-limiting toxicity (剂量限制性毒性)`), generously, so no key term is English-only. Never translate clauses or summary lines. A Chinese 口诀 (mnemonic) only when asked. English stays primary; titles and filenames stay canonical.
- **When ingesting a source into a page, show the full page content in chat.** What goes on the page = exactly what the human reads in chat. Paste the complete page body (minus frontmatter), not highlights. This overrides "Answer short first" for ingests/digests.
- **Lint at each stopping point.** Run `python3 scripts/sync.py` (below). Silently fix mechanical issues (broken links, missing cross-links); surface judgment calls (a page possibly in the wrong folder, a debatable merge/split) to the human.
- **Commit & push on your own judgment — don't ask.** When a batch of work reaches a stopping point, commit with a descriptive message and push — to `main`, or to the session's assigned branch when one is given. Apply the Confidentiality scrub first; surface anything unexpected (failed deploy, sensitive-data catch).
- **Published site:** Quartz v4 → https://pzhang724.github.io/biostat-kb/ (auto-deploys on push to `main`).
- **Human:** clinical-trial biostatistician.

## Confidentiality — never commit sensitive data

**This overrides "capture faithfully" and "Save Q&A by default."** Before writing anything to `raw/`, `wiki/`, a commit message or any file, scrub:

- **Protocol / study / trial identifiers** — protocol numbers, study codes, internal trial IDs, IND/NDA numbers.
- **Drug / compound identifiers** — sponsor compound codes, investigational product names, program-identifying isotope/formulation codes.
- **Sponsor-confidential information** — unpublished program internals, pipeline specifics, non-public work details.
- **Patient data / PHI** — names, subject IDs, dates of birth, site-identifying details.

Handle it by **masking** in plain language ("some study", "a patient", "the study drug", "a sponsor"; bracketed placeholders like `[PROTOCOL]` where a slot must be explicit) or by **flagging** it ("this looks confidential — mask or skip?") and waiting. Keep pages at the level of public, generalizable knowledge. If sensitive data was saved, scrub the working tree immediately; if it reached a commit, stop and tell the human (history rewrite is their call).

## Layout

```
biostat-kb/
├── CLAUDE.md
├── raw/sources/  raw/assets/   # captures (unpublished provenance)
├── scripts/sync.py             # regenerates index/learning lists + lints
├── site/                       # Quartz v4 — touch only for site config changes
└── wiki/                       # what publishes
    ├── index.md                # catalog — lists are generated
    ├── learning.md             # dashboard — Learned / In Progress generated; To Learn by hand
    ├── log.md                  # append-only activity log
    ├── therapeutic-areas/      # main-narrative maps
    ├── clinical/               # diseases, biology, biomarkers, imaging, PK/dosimetry, clinical criteria
    ├── statistics/             # endpoints, design, estimands, missing data, analysis methods
    ├── trial-conduct/          # data standards + how a trial is run and recorded
    ├── regulatory/             # what regulators / ethics committees require
    └── templates/              # page templates (not published)
```

### Which folder

Pick the page's **primary** nature; link to the rest. Moving a page between folders never breaks `[[links]]` (Quartz resolves by title).

- `therapeutic-areas/` — a **map** (MOC, "map of content") at disease/area level that strings the terms together and adds no knowledge of its own. `Oncology` is the top map; indications (e.g. prostate cancer) are **sections within it**, promoted to their own page only if they grow large. A term is never a therapeutic area.
- `clinical/` — the disease and how it is judged: diseases, biology, biomarkers, imaging, treatments, PK/dosimetry, safety measurements, and clinical assessment criteria (RECIST 1.1, PCWG3, CTCAE, GINA, SAE/AESI, DLT).
- `statistics/` — endpoints, trial design (dose-finding, Simon two-stage), estimands and intercurrent events, missing data, analysis methods.
- `trial-conduct/` — how a trial is run and its data recorded: CDISC (SDTM, ADaM, controlled terminology), MedDRA/WHODrug, CRFs/ePRO, schedule of assessments, eligibility criteria, AE collection/follow-up.
- `regulatory/` — what regulators or ethics committees **require**: ICH guidelines, FDA/EMA guidance, IRB/IEC, Investigator's Brochure, protocol amendments, financial disclosure. (A statistical concept defined by ICH, like Estimand, stays in `statistics/`.)

## Learned / To-Learn

- **A page exists ⇔ the human has learned it or is learning it** (`status: learned | learning`).
- **To-learn items are not pages** — they are `- [ ]` lines in the **To Learn** section of `learning.md`, grouped by folder. Never pre-create stub pages.
- Chat remarks like "我在学 X" / "I finished X" are status directives: create the page as `learning`, flip `status:`, tick boxes. (That is distinct from chat-shared knowledge, which is captured first.)
- The Learned / In Progress lists are generated from `status:` by `scripts/sync.py` — change the page's `status:`, never the list.

## Page Conventions

```yaml
---
title: "Page Title"          # must equal the filename
type: concept                # or therapeutic-area (a map)
status: learning             # or learned
created: YYYY-MM-DD
---
```

That's all. No tags, source counts or `updated:` dates — the folder is the category, `log.md` is the provenance, and Quartz takes the modified date from git.

- **Links:** Obsidian wiki-links `[[Page Title]]`, anchors `[[Page Title#Section]]`. Every page links to at least one other page; when you create a page, also add inbound links from related pages (and from its therapeutic-area map). Never link a page that doesn't exist — unlearned items are plain-text checkboxes.
- **Filename = title, exactly** (Quartz slugifies both; a mismatch 404s). Use the readable title with spaces/parentheses: `Analysis Results Data ({cards}).md`. Rephrase to avoid `< > : " / \ | ? *`; never invent a kebab-case alternate. Always reference the exact canonical title.
- **Meta files** (`index.md`, `learning.md`, `log.md`) are the exception: Quartz resolves links by filename, so link the dashboard as `[[learning|Learning Dashboard]]`.

## Workflows

### Ingest (default: light touch)

1. **Capture** to `raw/` (see Sources).
2. **Write** or extend the content page(s) in the right folder — only what the human engaged with, typically 1–4 pages. Add the cross-links (related pages + the therapeutic-area map).
3. If a to-learn checkbox matches, tick it in `learning.md`.
4. **Sync:** `python3 scripts/sync.py` — regenerates the index and dashboard lists and lints. Fix any ERROR before moving on.
5. **Log:** append one line per ingest to `wiki/log.md` under today's `## YYYY-MM-DD` heading (append with the shell; no need to read the whole file):
   `- <page(s)> — new | extended | status → learned ← raw/sources/<file>.md`

### Query

Read the relevant pages (find them via `index.md`), answer with `[[Page Title]]` citations, short first.

### Learning Review

"What should I learn next?" → read `learning.md` and `index.md`; propose 2–3 items, one line of rationale each, favouring ones that connect to learned pages.

### Lint

`python3 scripts/sync.py` checks broken links, filename/title mismatches, pages outside the five folders, bad status/type, and orphans. Beyond that, look for pages in the wrong folder and missing links between clearly related pages. When the human asks for a lint, report a numbered checklist.
