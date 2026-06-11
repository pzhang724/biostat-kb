<!--
═══════════════════════════════════════════════════════════════════
HOW TO USE THIS TEMPLATE
═══════════════════════════════════════════════════════════════════
This is a generalized template of the biostat-kb operating schema —
a personal "learning ledger" wiki maintained by Claude, published
with Quartz v4.

To adopt it for a new person/repo:

1. Copy this file to the new repo root as `CLAUDE.md`.
2. Replace every `{{...}}` placeholder:
   - {{REPO_NAME}}     — the repository name (e.g. `biostat-kb`)
   - {{OWNER_ROLE}}    — who the wiki is for (e.g. `a clinical-trial
                         biostatistician`, `a frontend engineer`)
   - {{DOMAIN_TAGS}}   — the controlled tag vocabulary: 5–9 domains
                         covering the owner's field, e.g.
                         `biology` · `medical` · `statistics` ·
                         `standards` · `regulatory` ·
                         `data-management` · `trial-conduct`
   - {{N_DOMAINS}}     — how many tags are in that list
3. Create the matching folder skeleton (see Repository Layout):
   `raw/assets/`, `raw/sources/`, `wiki/` with `index.md`,
   `learning.md`, `log.md`, and the `sources/ concepts/ entities/
   topics/ templates/` subfolders, plus the Quartz site in `site/`.
4. Adjust the publishing notes (Quartz, GitHub Pages workflow) if a
   different static-site setup is used.
5. Delete this comment block.

Design intent worth preserving when adapting:
- The wiki is a LEARNING LEDGER, not an encyclopedia — pages are
  terse markers that learning happened, never summaries to read
  instead of the source.
- Knowledge enters ONLY as human-supplied sources (link / upload /
  chat-shared), captured to `raw/` first.
- Page exists ⇔ learned (or actively learning); to-learn items are
  checkboxes, not pages.
═══════════════════════════════════════════════════════════════════
-->

# CLAUDE.md — {{REPO_NAME}} Operating Schema

This is the operating schema for `{{REPO_NAME}}`, a personal **learning ledger** for {{OWNER_ROLE}}. You (Claude) maintain the `wiki/` directory. The human curates `raw/` sources and directs what to ingest. You never modify or delete a human-authored file in `raw/` — your only writes to `raw/` are creating new capture files (fetched link copies, saved uploads, chat-shared knowledge; see "Everything the human gives you is a source").

## Purpose — read this first

This wiki is **NOT an encyclopedia**. Its purpose is to let the human:

1. **Confirm what they have learned** — a page existing means "I learned this";
2. **See what they have not learned yet** — tracked as to-learn checklists;
3. **Navigate connections** between learned items via wiki-links (rendered as backlinks/graph by Quartz).

Consequences for how you write:

- **Be terse.** Pages are evidence of learning, not substitutes for the source. A source note is ≤ 15 bullet lines. A concept page is a definition plus a handful of key points plus links — never textbook prose.
- **Do not over-summarize.** The human digests the material themselves; you record that it happened and wire up the links. When in doubt, write less and link more. A page the human reads *instead of* the source defeats the purpose — pages are markers, not replacements.
- **Never fabricate coverage.** Only create or expand a page for material the human actually ingested or explicitly said they learned.

## Everything the human gives you is a source

The wiki records what the human has **already** learned. They learn from the original material themselves — **your summaries are not a substitute for that** (if they didn't read the source, they didn't learn it, no matter what you wrote). So a wiki page is a terse **marker that learning happened**, plus links — never a summary meant to be read in place of the source.

The human provides material in exactly **three forms**, and all become sources:

1. **A link (URL)** — fetch it, save a captured copy to `raw/sources/`, then ingest.
2. **Uploaded files / pictures** — save the file to `raw/sources/` (documents/notes) or `raw/assets/` (images/PDFs), then ingest.
3. **Knowledge shared in chat** — when the human states or pastes knowledge in conversation (e.g. "hey, this might be useful", relaying something they learned at work, a snippet with their own commentary): capture *their words* faithfully to a new file in `raw/sources/`, then ingest. This is the one write to `raw/` you are allowed. Capture what they said, not your elaboration of it.

Rules:

- **Never invent the source.** Knowledge enters only through these three forms. Do not write knowledge into the wiki that the human didn't supply this way — in particular, your own explanations during chat are not a source.
- **Distinguish material from commands.** "ingest X", "lint the wiki", "what should I learn next", "restructure this" are instructions — execute them, don't save them. If it's ambiguous whether a chat remark is material to keep or just conversation, ask before capturing.
- **Capture faithfully.** The raw copy is the original; the wiki page is the terse digested marker. Both are kept.

Capture file convention: `raw/sources/YYYY-MM-DD <short topic>.md`, first line noting origin (e.g. `Source: <url>, captured <date>`, `Uploaded file, <date>`, or `From chat, <date>`).

## Repository Layout

```
{{REPO_NAME}}/
├── CLAUDE.md            # This file
├── raw/
│   ├── assets/          # PDFs, images (human-managed, read-only for you)
│   └── sources/         # Raw clipped articles + notes captured from chat (don't edit human-authored ones)
├── site/                # Quartz v4 framework — do not touch except for site config changes
├── wiki/                # You maintain everything below
│   ├── index.md         # Catalog of all pages — update on every ingest
│   ├── learning.md      # Learning dashboard: Learned / In Progress / To Learn
│   ├── log.md           # Append-only activity log
│   ├── sources/         # One short note per ingested raw source
│   ├── concepts/        # Methods, standards, frameworks, domain concepts
│   ├── entities/        # People, software/packages, organizations, key documents
│   ├── topics/          # Maps of Content (MOCs): per-domain learning maps
│   └── templates/       # Page templates (reference only — not published, do not modify)
└── .github/workflows/   # Pushing to main auto-deploys wiki/ to GitHub Pages
```

## Domain Context

Knowledge spans {{N_DOMAINS}} domains (this is also the controlled tag vocabulary):

{{DOMAIN_TAGS}}

Most pages are cross-domain — tag each page with 1–3 domains from this exact list. **Never invent new domain tags.** Additional free-form tags are allowed after the domain tags but keep them rare.

## The Learned / To-Learn Layer

This is the core mechanism of the wiki:

- **A wiki page exists ⇔ the human has learned it (or is actively learning it).** Frontmatter `status:` is `learning` or `learned`.
- **To-learn items are NOT pages.** They live as `- [ ]` checklist entries inside topic (MOC) pages, and the highest-priority ones are mirrored in `wiki/learning.md`.
- **When the human learns something**: check the box in the topic page, create the page (status `learning` or `learned` as directed), link it from related pages, update `learning.md` and `index.md`.
- **Chat remarks are progress signals.** When the human mentions in conversation "I'm learning X" / "I finished X" (in any language), treat it as a directive to update this layer (create the page as `learning`, flip status, check boxes) — no link or upload needed for a status change. This is distinct from chat-shared *knowledge*, which gets captured to `raw/sources/` first.
- Do not pre-create stub pages for unlearned material — an unlearned item is a checkbox, not a page.

`wiki/learning.md` has three sections — **Learned** (links to pages with status `learned`), **In Progress** (status `learning`), **To Learn** (checklist, grouped by topic). Keep it in sync whenever any page's status changes.

## Page Conventions

### YAML Frontmatter

```yaml
---
title: "Page Title"
type: source | concept | entity | topic
status: learning | learned        # not used on type: source pages
tags: [tag-1, tag-2]              # 1–3 from the domain vocabulary
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: 1                        # count of raw sources that informed this page
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

Folder placement: `sources/` one note per raw source · `concepts/` methods, standards, domain concepts · `entities/` people, packages, organizations, key documents · `topics/` MOCs and syntheses.

## Workflows

### Capture (when the human supplies a link, uploads a file/picture, or shares knowledge in chat)

1. For a link: fetch it and save a captured copy to `raw/sources/YYYY-MM-DD <short topic>.md` (origin line `Source: <url>, captured <date>`). For an upload: save it to `raw/sources/` (notes/docs) or `raw/assets/` (images/PDFs). For chat-shared knowledge: save the human's words to `raw/sources/YYYY-MM-DD <short topic>.md` (origin line `From chat, <date>`).
2. Continue straight into the Ingest workflow on that new file.

### Ingest (default: light touch)

When told to ingest a source (or right after Capture):

1. **Read** the raw file in `raw/sources/`.
2. **Create** a short source note in `wiki/sources/` (template: `source-note.md`, ≤ 15 bullet lines).
3. **Create or update** concept/entity pages **only for what the human actually engaged with** — typically 1–4 pages, not an exhaustive sweep. Ask if unsure what they consider "learned" from it.
4. **Check off** any matching to-learn items in topic pages and `learning.md`.
5. **Update** `wiki/index.md`; **append** to `wiki/log.md`.

### Query

1. Read `wiki/index.md` (and `learning.md` if the question concerns progress).
2. Read the relevant pages in full; synthesize with `[[Page Title]]` citations.
3. **Answer short first.** The human follows up quickly — give the direct answer, not an exposition; let the follow-ups pull out detail.

### Learning Review

When asked "what should I learn next" (or similar): read `learning.md` and topic MOCs, propose 2–3 next items with a one-line rationale each, considering what learned pages they would connect to.

### Lint

When told to "lint the wiki": check for broken wiki-links, filename/title mismatches, orphan pages, status/dashboard drift between pages and `learning.md`, stale checkboxes (item learned but box unchecked), and missing links between clearly related pages. Report as a numbered checklist; fix only when told.

## Log Format

Append to `wiki/log.md`, newest entry at the bottom:

```
## YYYY-MM-DD
- Ingested `raw/sources/<file>` → [[Source Note Title]]; created [[X]], updated [[Y]]
- Marked [[Z]] as learned; checked off in [[Topic]] and learning.md
```
