# raw/

Immutable source material. You add files here. AI reads them. Nobody edits them in place.

## Subfolders

- `articles/` — research docs, web clips, agreements, PDFs
- `data/` — CSVs, JSON exports, datasets
- `screenshots/` — images of competitor products, design inspiration, etc. - direct destination for your OS screenshot tool
- `transcripts/` — meeting transcripts, voice notes, call recordings
- `uploads/` — files dropped here for AI context (anything that doesn't fit above)


## Rules

- **Never edit a file in raw/.** If you need to correct something, add a new version with a suffix (`-v2`, `-corrected`).
- **Name files descriptively.** `2026-05-26-client-call-acme.md` beats `notes.md`.
- **AI reads raw/ during Ingest and Compile operations.** It summarizes into `wiki/` — that's where the knowledge lives.
