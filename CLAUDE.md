# LLM Wiki — Schema & Operating Manual

This file is the **schema** for a compounding, LLM-maintained wiki. It defines the
structure, conventions, and workflows. When you (Claude) work in this directory,
follow this document exactly. It is the source of truth for *how* the wiki works;
the wiki pages are the source of truth for *what it knows*.

Based on Andrej Karpathy's "LLM Wiki" pattern
(https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) and aligned
with the **Open Knowledge Format (OKF) v0.2**
(https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md).

**Schema version: 2.0** — v2 makes the wiki OKF-conformant (formal `type`
conformance, OKF lifecycle values, an optional trust family, and `stale_after`)
while keeping the wiki's link-centric simplicity. See the changelog at the bottom.

---

## 1. What this wiki is about

**Topic:** The **LLM-Wiki concept itself** — the pattern of an AI incrementally
building and maintaining a persistent knowledge base as an alternative to
re-running RAG on every query, plus the surrounding ideas (persistent memory,
compounding artifacts, knowledge-base agents, RAG comparisons, real
implementations like OKF, and tooling).

**Purpose:** A curated, cross-referenced reference that compounds over time.
Every source added should make the wiki *richer*, not just longer.

**Nature of sources:** **Mostly external links** — gists, blog posts, papers,
docs, repos, threads, videos. Because sources are links, we **capture their
substance at ingestion time** (quotes, claims, summary) so the wiki survives link
rot. The link is the pointer; the source note is the durable record.

---

## 2. Three-layer architecture

1. **Raw sources** (`sources/`) — one note per external link. Immutable *record*
   of what a source said. We never rewrite a source's captured content to fit our
   conclusions; if we disagree, we say so on a concept page, not by editing the
   source note.
2. **The wiki** (`concepts/`, `entities/`, `summaries/`) — LLM-generated pages
   that synthesize across sources. This is where compounding happens.
3. **The schema** (this file) — structure, conventions, workflows.

This directory is an **OKF Knowledge Bundle** (§9). Navigation lives in `index.md`
(catalog by category) and `log.md` (append-only chronological change log).

---

## 3. Directory layout

```
llm-wiki-wiki/
  CLAUDE.md          # this schema (not a wiki page; exempt from conformance)
  index.md           # reserved: catalog of every page, grouped by category
  log.md             # reserved: append-only change log (newest at bottom)
  sources/           # one note per external link  → source-<slug>.md
  concepts/          # ideas, patterns, workflows   → <slug>.md
  entities/          # people, projects, tools, repos → <slug>.md
  summaries/         # cross-cutting synthesis / overview pages → <slug>.md
```

Create a folder the first time it's needed; don't pre-create empty ones.

---

## 4. Page conventions

### 4.1 Slugs & filenames
- **kebab-case**, lowercase, ASCII: `three-layer-architecture.md`.
- Source notes are prefixed: `source-<slug>.md` (e.g. `source-karpathy-llm-wiki-gist.md`).
- One concept/entity per file. Split rather than let a page sprawl.

### 4.2 Front matter (YAML) — required on every non-reserved page
`type` is the **only mandatory field** (this is what OKF conformance turns on).
Everything else is optional, but the fields below are the house standard:
```yaml
---
type: source | concept | entity | summary   # REQUIRED, non-empty
title: Human-readable title
tags: [rag, memory, pattern]                 # lowercase kebab tags
status: draft | stable | deprecated          # OKF lifecycle; default stable
created: YYYY-MM-DD
updated: YYYY-MM-DD
stale_after: YYYY-MM-DDTHH:MM:SSZ            # optional; page is stale past this instant
sources: [source-karpathy-llm-wiki-gist]     # slugs of source notes this page draws on
# Optional OKF trust family (see §9.2):
generated: { by: claude-code/opus-4.8, at: YYYY-MM-DDTHH:MM:SSZ }
verified:
  - { by: human:mark, at: YYYY-MM-DDTHH:MM:SSZ }
---
```
Source notes add these fields instead of `sources:`:
```yaml
url: https://...
author: Name or handle (or "unknown")
published: YYYY-MM-DD | unknown
accessed: YYYY-MM-DD                 # when we captured it
source_type: gist | blog | paper | repo | docs | thread | video | other
link_status: live | dead | paywalled | archived
archive_url: https://web.archive.org/...   # optional, when captured
```
A page with `status` absent is treated as `stable` (OKF default). "Stub" pages use
`status: draft` and say so in the body.

### 4.3 Cross-references
- Link between wiki pages with **relative Markdown links** (clickable in the
  terminal): `[Three-layer architecture](concepts/three-layer-architecture.md)`.
  (OKF also permits bundle-relative absolute `/path` links; we use relative for
  terminal-clickability. Consumers must tolerate broken links.)
- Every substantive claim on a concept/summary page should trace to at least one
  source note via an inline link or the `sources:` field.
- Prefer **many small links** over one dense paragraph — cross-linking is the
  point of this wiki.

### 4.4 Source note body structure
```
# <Title>   ·   <url as a link>

**One-line what-it-is.**

## Summary
2–6 sentences capturing the core argument in our words.

## Key claims / quotes
- "≤15-word verbatim quote" — attributed, used sparingly (respect copyright).
- Paraphrased claim → links to the concept page it feeds.

## Why it matters here
How this source advances the wiki's topic; what it confirms or contradicts.

## Feeds
- [Concept page A](../concepts/a.md)
- [Entity B](../entities/b.md)
```
Keep verbatim quoting minimal: at most one short quote per idea, attributed.
Capture *substance in our own words* so the note survives if the link dies.

---

## 5. Core operations

### 5.1 Ingestion (adding a source/link)
1. **Fetch & read** the link (WebFetch or the browser tools). If it can't be
   reached, mark `link_status` accordingly and capture whatever is available
   (archive.org, cache, user-provided text).
2. **Create** `sources/source-<slug>.md` using the source-note structure. Fill
   all front-matter fields; set `accessed` to today.
3. **Integrate**: update or create the relevant `concepts/` and `entities/`
   pages. Add cross-links both ways (source ↔ concept). If a claim **contradicts**
   an existing page, don't silently overwrite — record both and note the tension
   (see 5.3).
4. **Index**: add/refresh the page's entry in `index.md`.
5. **Log**: append one entry to `log.md` (format in §6).

### 5.2 Querying (answering a question)
1. **Search the wiki first** (`index.md`, then grep across `concepts/` and
   `summaries/`). Answer from the wiki when it already knows.
2. Cite the pages you used so the answer is traceable.
3. If synthesizing produced a **new, reusable insight**, file it back as a new
   concept/summary page (and log it). Queries should *grow* the wiki, not just
   consume it.
4. If the wiki can't answer, say so and propose which source(s) to ingest next.

### 5.3 Maintenance / lint (periodic health check)
Run when asked, or opportunistically. Check for:
- **Conformance** — every non-reserved `.md` has parseable frontmatter with a
  non-empty `type`; reserved files (`index.md`, `log.md`) follow their structures
  (§9.3).
- **Contradictions** — conflicting claims across pages; surface and reconcile, or
  document the disagreement explicitly on the relevant concept page.
- **Stale claims** — `stale_after` reached, or `updated` far in the past on a
  fast-moving topic; re-verify.
- **Link rot** — re-check source `url`s; flip `link_status` and add an
  `archive_url` when a link dies. This is a first-class concern here.
- **Orphaned pages** — pages nothing links to; wire them in or retire them.
- **Missing cross-references** — related pages that should link and don't.
- **Index drift** — `index.md` entries that don't match files on disk.
Record every maintenance action as a `maintenance` log entry.

---

## 6. Log format (`log.md`)

Append-only, newest at the bottom, one block per action, machine-parseable:

```
## YYYY-MM-DD  ·  <ingest | query | synthesize | maintenance>
- action: <verb phrase, e.g. "ingested Karpathy LLM Wiki gist">
- pages: [source-karpathy-llm-wiki-gist, concepts/three-layer-architecture]
- note: <one line of context or rationale>
```

Never edit or delete past log entries; correct via a new entry.

---

## 7. Index format (`index.md`)

A reserved file: a catalog grouped by category. Each line links to the page and
gives a one-line hook. The **root `index.md` is the one place** a bundle-level
frontmatter block is allowed, and it declares the OKF version:

```
---
okf_version: "0.2"
title: Index
---

## Concepts
- [Three-layer architecture](concepts/three-layer-architecture.md) — sources / wiki / schema layering.
...
```

Keep the index in sync on every ingestion and page creation.

---

## 8. House rules

- **Sources are read, never rewritten to fit conclusions.** Disagreement lives on
  concept pages.
- **Everything traces to a source.** No free-floating claims on synthesis pages.
- **Compounding over volume.** A good ingestion strengthens links and reconciles
  claims, not just adds a file.
- **Capture substance, not just the URL** — assume every link may die.
- **Respect copyright**: short attributed quotes only, summaries in our own words.
- **Log every mutation.** If it changed the wiki, it has a log entry.
- **This file (`CLAUDE.md`) is the schema, not content.** It is exempt from
  conformance. Update it deliberately when conventions change, note the change in
  `log.md`, and bump the schema version in the header + changelog.

---

## 9. OKF conformance

This bundle targets **OKF v0.2**. The format is deliberately a *superset* of what
a personal wiki needs, so we adopt the parts that add real value (conformance,
lifecycle, trust) and keep the rest optional.

### 9.1 Field mapping (our schema ↔ OKF)
| Purpose | This wiki | OKF v0.2 |
|---|---|---|
| Kind of page | `type` (closed set: concept/entity/summary/source) | `type` (open; producer-defined) |
| Catalog | `index.md` | `index.md` (reserved) |
| History | `log.md` | `log.md` (reserved) |
| Provenance | `sources:` (slugs) + source-note `url`/`author`/`accessed` | `sources:` family (id/resource/author/…) |
| Lifecycle | `status: draft/stable/deprecated`, `stale_after` | same |
| Trust | `generated`, `verified` (optional) | same |
| Linking | relative markdown links | markdown links (bundle-relative preferred) |

### 9.2 Trust family (optional but encouraged on synthesis pages)
- `generated: { by, at }` — who/what created the content.
- `verified: [{ by, at }, ...]` — independent confirmations.
- **Actor convention:** `<producer>/<version>` for agents/tools (e.g.
  `claude-code/opus-4.8`), `human:<id>` for people (e.g. `human:mark`),
  `process:<id>` for workflows. A `human:` verifier promotes a page to the
  **human-reviewed** trust tier; a non-human verifier → **machine-confirmed**; no
  `verified` → **unverified**.
- Use trust metadata to blunt the
  [hallucination-baking risk](concepts/hallucination-baking-risk.md): a reader (or
  agent) can gate on tier and on `stale_after`.

### 9.3 Minimal conformance rule
A bundle conforms if:
1. Every non-reserved `.md` file has parseable YAML frontmatter with a non-empty
   `type`.
2. Reserved files (`index.md`, `log.md`) follow their structures (§6–§7).
3. Consumers tolerate missing optional fields, unknown `type` values, unknown
   keys, and broken links.
`CLAUDE.md` is schema, not a concept, and is exempt.

### 9.4 What we deliberately do NOT adopt (yet)
- **Attested Computation** — this is a link-reference wiki with no computed values
  to attest; adopt only if the wiki starts carrying data/metrics.
- **Per-claim footnote provenance** — our page-level `sources:` is enough for a
  curated link wiki; escalate to footnote-keyed claims only if a page's factual
  precision demands it.
- **Open/arbitrary `type`s** — we keep a closed set of four page types for
  legibility. (A consumer reading us as OKF still sees valid `type` values.)

---

## Changelog
- **2.0** (2026-09-02) — OKF v0.2 alignment: `type` conformance rule; lifecycle
  values switched to OKF's `draft/stable/deprecated` (migrated `stub` → `draft`);
  added optional `stale_after` and the `generated`/`verified` trust family with the
  actor convention; `index.md` now declares `okf_version`. Added §9.
- **1.0** (2026-09-02) — Initial schema: three-layer architecture, page
  conventions, ingestion/query/maintenance workflows, index + log formats.
```

---

_Seed source:_ Karpathy's gist —
https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
