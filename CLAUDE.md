# CLAUDE.md — biostat-kb Operating Schema

This is the operating schema for `biostat-kb`, a personal **learning ledger** for a clinical-trial biostatistician. You (Claude) maintain the `wiki/` directory. The human curates `raw/` sources and directs what to ingest. You never modify or delete a human-authored file in `raw/` — your only writes to `raw/` are creating new capture files (fetched link copies, saved uploads, chat-shared knowledge; see "Everything the human gives you is a source").

## Purpose — read this first

This wiki is **NOT an encyclopedia**. Its purpose is to let the human:

1. **Confirm what they have learned** — a page existing means "I learned this";
2. **See what they have not learned yet** — tracked as to-learn checklists;
3. **Navigate connections** between learned items via wiki-links (rendered as backlinks/graph by Quartz).

Consequences for how you write:

- **Be terse.** Pages are evidence of learning, not substitutes for the source. A content page is a definition plus a handful of key points plus links — never textbook prose.
- **Do not over-summarize.** The human digests the material themselves; you record that it happened and wire up the links. When in doubt, write less and link more. A page the human reads *instead of* the source defeats the purpose — pages are markers, not replacements.
- **Never fabricate coverage.** Only create or expand a page for material the human actually ingested or explicitly said they learned.

## Everything the human gives you is a source

The wiki records what the human has **already** learned. They learn from the original material themselves — **your summaries are not a substitute for that** (if they didn't read the source, they didn't learn it, no matter what you wrote). So a wiki page is a terse **marker that learning happened**, plus links — never a summary meant to be read in place of the source.

The human provides material in exactly **three forms**, and all become sources:

1. **A link (URL)** — fetch it, save a captured copy to `raw/sources/`, then ingest.
2. **Uploaded files / pictures** — save the file to `raw/sources/` (documents/notes) or `raw/assets/` (images/PDFs), then ingest.
3. **Knowledge shared in chat** — when the human states or pastes knowledge in conversation (e.g. "诶，这个可能有用", relaying something they learned at work, a snippet with their own commentary): capture *their words* faithfully to a new file in `raw/sources/`, then ingest. This is the one write to `raw/` you are allowed. Capture what they said, not your elaboration of it.

Rules:

- **Never invent the source.** Knowledge enters only through these three forms. Do not write knowledge into the wiki that the human didn't supply this way — in particular, your own explanations during chat are not a source.
- **Distinguish material from commands.** "ingest X", "lint the wiki", "what should I learn next", "restructure this" are instructions — execute them, don't save them. If it's ambiguous whether a chat remark is material to keep or just conversation, ask before capturing.
- **Capture faithfully.** The raw copy is the original; the wiki page is the terse digested marker. Both are kept.

Capture file convention: `raw/sources/YYYY-MM-DD <short topic>.md`, first line noting origin (e.g. `Source: <url>, captured <date>`, `Uploaded file, <date>`, or `From chat, <date>`).

**Raw captures are provenance only — they are NOT published.** The wiki does **not** keep a per-source note page (the old `wiki/sources/` layer was removed). The `raw/sources/` capture *is* the saved source; the published marker of learning is the content page (in one of the four layer folders below) plus the `wiki/log.md` entry that records which raw capture it came from. Do not recreate a published per-source-note layer.

## User Preferences & Notes

Durable preferences live **here** (in the repo), not in external/per-machine memory — the human may switch machines and the repo travels with them. Add new ones to this section.

- **Save Q&A by default — and never ask whether to.** When the human asks a substantive question and you answer, capture that Q&A as a raw source (`From chat, <date>`) and run a light-touch ingest — without asking each time. This includes **follow-up and clarification questions**: the human has confirmed they don't ask things casually, so every substantive question they ask counts as material to keep. Do not pause to ask "should I record this?" — just do it. This **extends form #3 above**: for this human, their question + the ensuing answer *is* material worth keeping (it overrides the general "your chat explanations aren't a source / ask before capturing" caution). Still execute pure commands ("ingest X", "lint", "what next") as instructions, not material.
- **Answer short first, expect follow-ups.** Keep the first answer to a short paragraph (~4–6 sentences or a few short bullets) — direct answer plus a little context, not a one-liner and not an exposition. The human follows up quickly to pull out detail. Applies to all chat, not just the Query workflow.
- **Capture/ingest first, answer last.** Do the recording (capture + ingest + index/log/dashboard updates) BEFORE delivering the answer, so the substantive answer is the final thing in the turn — the human shouldn't have to scroll up past tool calls to re-find it. A one-line note like "记录并 ingest" before the tool calls is fine; the real answer goes at the bottom. (This reorders, but does not relax, "Save Q&A by default" or "Answer short first".)
- **Chinese annotations are welcome in wiki pages.** When it aids the human's understanding, add a brief Chinese gloss next to an English term — inline parenthetical (e.g. `lesion (病灶)`) for a key term, or a short Chinese note for a tricky concept. Use judgment: annotate where it genuinely helps (jargon, non-obvious translations), don't gloss everything. English remains the primary text; titles/filenames stay in their canonical (usually English) form.
- **Published site:** Quartz v4 → https://pzhang724.github.io/biostat-kb/ (auto-deploys on push to `main`).
- **Human:** clinical-trial biostatistician.

## Confidentiality — never commit sensitive data

**This rule overrides "Capture faithfully" and "Save Q&A by default."** Before writing anything to `raw/`, `wiki/`, `log.md`, a commit message, or any file, scrub sensitive identifiers — when in doubt, mask and ask rather than store.

Treat as sensitive and **never persist verbatim**:

- **Protocol / study / trial identifiers** — protocol numbers (e.g. `XXX-020-001`), study codes, internal trial IDs, IND/NDA numbers.
- **Drug / compound identifiers** — sponsor compound codes, investigational product names, isotope/formulation codes that identify a specific program.
- **Sponsor-confidential information** — unpublished company/program internals, pipeline specifics, anything the human relays from work that isn't public.
- **Patient data** — any patient-level data or PHI: names, subject/patient IDs, dates of birth, site-identifying details, etc.

How to handle when such content appears (in chat, a pasted snippet, an uploaded file, or a draft page):

1. **Mask it** — refer to it generically in plain language: "some study", "a patient", "the study drug", "a sponsor" (the human prefers this natural phrasing over bracketed tokens). Keep only the transferable, non-identifying methodology/concept. Bracketed placeholders (`[PROTOCOL]`, `[SUBJECT ID]`) are fine where a slot needs to be explicit.
2. **Or flag it** — tell the human "this looks confidential — mask or skip?" and wait, rather than capturing it.
3. Keep wiki pages at the level of **public, generalizable knowledge** (methods, standards, CDISC, statistical concepts). Identifying specifics never belong in a repo that auto-deploys to public GitHub Pages.

If sensitive data has already been saved, scrub it from the working tree immediately; if it ever reaches a commit, stop and tell the human (history rewrite is their call).

## Repository Layout

```
biostat-kb/
├── CLAUDE.md            # This file
├── raw/
│   ├── assets/          # PDFs, images (human-managed, read-only for you)
│   └── sources/         # Raw clipped articles + notes captured from chat (don't edit human-authored ones)
├── site/                # Quartz v4 framework — do not touch except for site config changes
├── wiki/                # You maintain everything below (this is what publishes)
│   ├── index.md         # Catalog of all pages, grouped by layer — update on every ingest
│   ├── learning.md      # Learning dashboard: Learned / In Progress / To Learn
│   ├── log.md           # Append-only activity log
│   ├── therapeutic-areas/   # Clinical/disease/oncology: diseases, biology, imaging, response criteria
│   ├── statistics/          # Statistical & methodological concepts: endpoints, estimands, PK/exposure
│   ├── data-standards/      # CDISC and data standards: SDTM, ADaM, controlled terminology
│   ├── regulatory-guidance/ # Regulatory guidances/frameworks: ICH, FDA/EMA guidance documents
│   └── templates/       # Page templates (reference only — not published, do not modify)
└── .github/workflows/   # Pushing to main auto-deploys wiki/ to GitHub Pages
```

## Domain Context

Knowledge spans seven domains (this is also the controlled tag vocabulary):

`biology` · `medical` · `statistics` · `standards` · `regulatory` · `data-management` · `trial-conduct`

Most pages are cross-domain — tag each page with 1–3 domains from this exact list. **Never invent new domain tags.** Additional free-form tags are allowed after the domain tags but keep them rare.

## The Learned / To-Learn Layer

This is the core mechanism of the wiki:

- **A wiki page exists ⇔ the human has learned it (or is actively learning it).** Frontmatter `status:` is `learning` or `learned`.
- **To-learn items are NOT pages.** They live as `- [ ]` checklist entries in the **To Learn** section of `wiki/learning.md`, grouped by layer/topic.
- **When the human learns something**: check the box in `learning.md`, create the page (status `learning` or `learned` as directed) in the right layer folder, link it from related pages, update `learning.md` and `index.md`.
- **Chat remarks are progress signals.** When the human mentions in conversation "我在学 X" / "I'm learning X" / "I finished X", treat it as a directive to update this layer (create the page as `learning`, flip status, check boxes) — no link or upload needed for a status change. This is distinct from chat-shared *knowledge*, which gets captured to `raw/sources/` first.
- Do not pre-create stub pages for unlearned material — an unlearned item is a checkbox, not a page.

`wiki/learning.md` has three sections — **Learned** (links to pages with status `learned`), **In Progress** (status `learning`), **To Learn** (checklist, grouped by topic). Keep it in sync whenever any page's status changes.

## Page Conventions

### YAML Frontmatter

```yaml
---
title: "Page Title"
type: concept                     # all content pages; the layer folder encodes the category
status: learning | learned
tags: [medical, statistics]       # 1–3 from the domain vocabulary
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: 1                        # count of raw captures that informed this page
---
```

### Cross-References

- Use Obsidian wiki-links: `[[Page Title]]`; section anchors as `[[Page Title#Section]]`.
- Every page should link to at least one other existing wiki page (skip only while the wiki is nearly empty).
- When you create a new page, add inbound links to it from existing related pages.
- **Links must resolve.** Never wiki-link a page that doesn't exist — unlearned items are plain-text checkboxes, not links.

### File Naming

**Critical: the filename basename must equal the frontmatter `title`** — Quartz slugifies link text and filename identically; if they differ the published link 404s.

- Use the readable title as the filename, including spaces, parentheses, em-dashes, curly braces: `Analysis Results Data ({cards}).md`.
- Sanitize Windows-illegal chars (`< > : " / \ | ? *`) by rephrasing the title — do not invent a kebab-case alternate.
- When referencing a page, use the **exact** canonical title. One canonical title per file; fix variant references rather than tolerating them.
- **Meta files are the exception** (`index.md`, `learning.md`, `log.md`): their filenames intentionally differ from their titles ("Wiki Index", "Learning Dashboard", "Activity Log"). Quartz resolves a `[[wiki-link]]` by **filename slug, not title**, so link the dashboard as `[[learning|Learning Dashboard]]` (not `[[Learning Dashboard]]`, which 404s). Content pages keep filename == title so plain `[[Title]]` works.

Folder placement — every content page lives in exactly one of four layer folders:

- `therapeutic-areas/` — clinical / disease / oncology knowledge: diseases, biology, imaging, response criteria (e.g. RECIST, PCWG3, PSA, PSMA PET).
- `statistics/` — statistical & methodological concepts: endpoints, estimands, intercurrent events, surrogate endpoints, PK, dosimetry.
- `data-standards/` — CDISC and data standards: SDTM, ADaM, controlled terminology.
- `regulatory-guidance/` — regulatory guidances & frameworks: ICH (e.g. E9(R1)), FDA/EMA guidance documents.

Many pages are cross-cutting — file under the **primary** layer and wiki-link to the others. Moving a page between folders does **not** break `[[wiki-links]]` (Quartz resolves by title, not path).

## Workflows

### Capture (when the human supplies a link, uploads a file/picture, or shares knowledge in chat)

1. For a link: fetch it and save a captured copy to `raw/sources/YYYY-MM-DD <short topic>.md` (origin line `Source: <url>, captured <date>`). For an upload: save it to `raw/sources/` (notes/docs) or `raw/assets/` (images/PDFs). For chat-shared knowledge: save the human's words to `raw/sources/YYYY-MM-DD <short topic>.md` (origin line `From chat, <date>`).
2. Continue straight into the Ingest workflow on that new file.

### Ingest (default: light touch)

When told to ingest a source (or right after Capture):

1. **Read** the raw file in `raw/sources/`.
2. **Create or update** content pages in the right layer folder (`therapeutic-areas/`, `statistics/`, `data-standards/`, `regulatory-guidance/`) **only for what the human actually engaged with** — typically 1–4 pages, not an exhaustive sweep. Ask if unsure what they consider "learned" from it. Do **not** create a published source-note page.
3. **Check off** any matching to-learn items in `learning.md`.
4. **Update** `wiki/index.md` (under the right layer section); **append** to `wiki/log.md`, naming the `raw/sources/` capture the page came from.

### Query

1. Read `wiki/index.md` (and `learning.md` if the question concerns progress).
2. Read the relevant pages in full; synthesize with `[[Page Title]]` citations.
3. **Answer short first.** The human follows up quickly — give the direct answer plus a little context (aim for a short paragraph, ~4-6 sentences, not a one-liner and not an exposition); let the follow-ups pull out detail.

### Learning Review

When asked "what should I learn next" (or similar): read `learning.md` and `index.md`, propose 2–3 next items with a one-line rationale each, considering what learned pages they would connect to.

### Lint

When told to "lint the wiki": check for broken wiki-links, filename/title mismatches, pages filed in the wrong layer folder, orphan pages, status/dashboard drift between pages and `learning.md`, stale checkboxes (item learned but box unchecked), index sections out of sync with the folders, and missing links between clearly related pages. Report as a numbered checklist; fix only when told.

## Log Format

Append to `wiki/log.md`, newest entry at the bottom:

```
## YYYY-MM-DD
- Ingested `raw/sources/<file>`; created [[X]] (statistics), updated [[Y]] (therapeutic-areas)
- Marked [[Z]] as learned; checked off in learning.md
```
