# biostat-kb

My learning ledger as a biostatistician — a record of what I've **already learned**, with the connections between topics. Live at **https://pzhang724.github.io/biostat-kb/**.

## How I use it

Give Claude material in one of three ways, then say "ingest it":

- **a link**,
- **a file / picture I upload**, or
- **something I tell it in chat** ("诶，这个可能有用") — Claude saves my words as a source first

Claude saves it to `raw/`, then writes a short marker page in `wiki/` and links it into what I already know. Pages are markers that I learned something — not summaries to read instead of the source.

## What's where

- `wiki/` — my knowledge (this is what gets published)
- `raw/` — original material I fed in (never edited, just kept for provenance)
- everything else — site machinery, ignore it

## Preview locally

```bash
cd site && npm ci && npx quartz build --directory ../wiki --output public --serve
```

Push to `main` → site rebuilds and deploys automatically.
