---
title: Three-layer architecture
type: concept
tags: [llm-wiki, pattern, architecture]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-karpathy-llm-wiki-gist, source-joshi-medium-llm-wiki]
---

# Three-layer architecture

The LLM-wiki pattern separates knowledge into three distinct layers, each with a
different owner and a different mutability rule. Keeping them separate is what lets
the wiki compound without corrupting its evidence base.

## At a glance

```mermaid
flowchart TB
    subgraph L3["Layer 3 · Schema — CLAUDE.md / AGENTS.md"]
        direction LR
        S["rules · conventions · ingest/query/lint workflows"]
    end
    subgraph L2["Layer 2 · The Wiki — LLM-owned"]
        direction LR
        W["concepts · entities · summaries · index.md · log.md"]
    end
    subgraph L1["Layer 1 · Raw Sources — immutable"]
        direction LR
        R["links · PDFs · notes  →  read, never modified"]
    end
    L1 -- "ingest = compile once" --> L2
    L3 -. "governs how the wiki behaves" .-> L2

    classDef raw fill:#e8f0fe,stroke:#4285f4,color:#111;
    classDef wiki fill:#e6f4ea,stroke:#34a853,color:#111;
    classDef schema fill:#fef7e0,stroke:#fbbc04,color:#111;
    class R raw; class W wiki; class S schema;
```

Raw sources are the *source code*, the wiki is the *compiled binary*, and the
schema is the *build configuration* — see [Knowledge as compilation](knowledge-compilation-analogy.md).

## The layers

1. **Raw sources** — Immutable, curated documents (articles, papers, data,
   and in this wiki, mostly *links*). The LLM **reads but never modifies** them.
   In this wiki they live as source notes in `sources/`, which capture each
   source's substance at ingestion time so the record survives link rot.
   See [Karpathy's gist](../sources/source-karpathy-llm-wiki-gist.md).

2. **The wiki** — LLM-generated Markdown the AI **fully manages**: summaries,
   entity pages, and concept pages (this file is one). This is the layer where
   cross-references and synthesis accumulate.

3. **The schema** — A configuration document (`CLAUDE.md` for Claude Code, or
   `AGENTS.md` for Codex-style agents) specifying structure, naming conventions,
   and the workflows for ingestion, querying, and maintenance. It governs *how* the
   wiki behaves; it is not itself wiki content.

The layering maps onto a [compilation analogy](knowledge-compilation-analogy.md):
raw sources are source code, the wiki is the compiled binary, and the schema is
the build configuration.

The **wiki layer** is exactly what the [Open Knowledge Format](open-knowledge-format.md)
standardizes — same markdown + YAML frontmatter, `index.md`, and `log.md` — turning
this personal pattern into an interoperable, exchangeable one.

## Why the separation matters
- **Evidence stays clean.** Because sources are never rewritten to fit
  conclusions, disagreements are recorded on wiki pages rather than hidden by
  editing the underlying record.
- **The wiki can be rebuilt.** If synthesis goes wrong, the source layer is intact
  and pages can be regenerated from it.
- **The schema is swappable.** Conventions can evolve without touching captured
  knowledge.

## Related
- [The three operations](three-operations.md) — ingest / query / lint over these layers.
- [Knowledge as compilation](knowledge-compilation-analogy.md) — the source-code → binary framing.
- [LLM Wiki vs traditional RAG](../summaries/llm-wiki-vs-rag.md) — why this layering compounds.
- Sources: [Karpathy — LLM Wiki gist](../sources/source-karpathy-llm-wiki-gist.md) · [Joshi — walkthrough](../sources/source-joshi-medium-llm-wiki.md)
