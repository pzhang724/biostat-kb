# CLAUDE.md — biostat-kb Operating Schema

This is the operating schema for `biostat-kb`, a personal **learning ledger** for a clinical-trial biostatistician. You (Claude) maintain the `wiki/` directory. The human curates `raw/` sources and directs what to ingest. You never modify or delete a human-authored file in `raw/` — your only write to `raw/` is creating new source files that capture the human's own chat input (see "Everything the human gives you is a source").

## Purpose — read this first

This wiki is **NOT an encyclopedia**. Its purpose is to let the human:

1. **Confirm what they have learned** — a page existing means "I learned this";
2. **See what they have not learned yet** — tracked as to-learn checklists;
3. **Navigate connections** between learned items via wiki-links (rendered as backlinks/graph by Quartz).

Consequences for how you write:

- **Be terse.** Pages are evidence of learning, not substitutes for the source. A source note is ≤ 15 bullet lines. A concept page is a definition plus a handful of key points plus links — never textbook prose.
- **Do not over-summarize.** The human digests the material themselves; you record that it happened and wire up the links. When in doubt, write less and link more.
- **Never fabricate coverage.** Only create or expand a page for material the human actually ingested or explicitly said they learned.

## Everything the human gives you is a source

Knowledge does not enter the wiki as conversation. If it isn't captured as a source, it has no provenance, doesn't persist, and can't be re-examined — it's wasted. So:

- **When the human conveys knowledge in chat** (a fact, their understanding, material to record), first **persist it verbatim** to `raw/sources/` as a dated personal note, *then* run the ingest workflow on it. Do NOT write chat narrative straight into wiki pages — that bypasses the source layer and breaks provenance.
- **Distinguish knowledge from commands.** Directions like "ingest X", "lint the wiki", "what should I learn next", "restructure this" are instructions, not sources — execute them, don't save them. If one message carries both knowledge and a command, extract the knowledge part into a source and act on the command.
- **Capture faithfully.** Save the human's own words with only light cleanup; the raw note is the original, the wiki page is the digested version. Both are kept.

Capture file convention: `raw/sources/YYYY-MM-DD <short topic>.md`, with a first line noting origin (`Personal note — conversation, <date>`).

## Repository Layout

```
biostat-kb/
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
│   ├── concepts/        # Methods, standards, frameworks, diseases, biology
│   ├── entities/        # People, R packages, software, organizations, guidances
│   ├── topics/          # Maps of Content (MOCs): per-domain or per-disease learning maps
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
- **To-learn items are NOT pages.** They live as `- [ ]` checklist entries inside topic (MOC) pages, and the highest-priority ones are mirrored in `wiki/learning.md`.
- **When the human learns something**: check the box in the topic page, create the page (status `learning` or `learned` as directed), link it from related pages, update `learning.md` and `index.md`.
- Do not pre-create stub pages for unlearned material — an unlearned item is a checkbox, not a page.

`wiki/learning.md` has three sections — **Learned** (links to pages with status `learned`), **In Progress** (status `learning`), **To Learn** (checklist, grouped by topic). Keep it in sync whenever any page's status changes.

## Page Conventions

### YAML Frontmatter

```yaml
---
title: "Page Title"
type: source | concept | entity | topic
status: learning | learned        # not used on type: source pages
tags: [medical, statistics]       # 1–3 from the domain vocabulary
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

Folder placement: `sources/` one note per raw source · `concepts/` methods, standards, diseases, biology · `entities/` people, packages, organizations, guidance documents · `topics/` MOCs and syntheses.

## Workflows

### Capture (when the human gives knowledge in chat)

1. Write their input verbatim (light cleanup only) to `raw/sources/YYYY-MM-DD <short topic>.md`, first line `Personal note — conversation, <date>`.
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
