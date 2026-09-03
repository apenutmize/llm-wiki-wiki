---
title: "Karpathy — LLM Wiki: Personal Knowledge Base Pattern"
type: source
tags: [llm-wiki, rag, memory, pattern, knowledge-base]
status: stable
created: 2026-09-02
updated: 2026-09-02
url: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
author: Andrej Karpathy
published: unknown
accessed: 2026-09-02
source_type: gist
link_status: live
---

# Karpathy — LLM Wiki: Personal Knowledge Base Pattern   ·   [gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)

**The seed idea for this wiki: an AI that incrementally builds and maintains a persistent wiki as an alternative to re-running RAG on every query.**

## Summary
Karpathy proposes replacing repeated retrieve-and-re-synthesize RAG with a
persistent, LLM-maintained wiki that sits between the user and raw source
materials. Instead of rediscovering cross-document connections on every query,
the system accumulates cross-references, contradictions, and synthesized insights
into a compounding artifact that grows richer with each source and interaction.
The design is organized as three layers (raw sources, the wiki, the schema),
driven by three operations (ingestion, querying, maintenance), and navigated via
an index catalog plus an append-only change log.

## Key claims / quotes
- The wiki is a "persistent, compounding artifact" — knowledge accumulates rather
  than being rediscovered per query. → [Compounding vs re-retrieval](../summaries/llm-wiki-vs-rag.md)
- Three layers: **raw sources** (immutable, read-only), **the wiki** (LLM-managed
  markdown), **the schema** (structure + conventions + workflows). → [Three-layer architecture](../concepts/three-layer-architecture.md)
- Three operations: **ingestion** (read → extract → update pages → log),
  **querying** (search wiki; file useful insights back as pages), **maintenance**
  (check contradictions, stale claims, orphans, missing cross-refs).
- Navigation: an **index** organized by category + an **append-only log** with a
  standardized, parseable entry format.
- Applications named: personal development tracking, academic research, literature
  analysis, team knowledge management, specialized deep-dives.

## Why it matters here
This is the origin document for the entire wiki — its schema, layering, and
workflows are derived directly from it. Every convention in `CLAUDE.md` traces
back here. It frames the core thesis the wiki exists to explore: knowledge that
**compounds** beats knowledge that is **re-retrieved**.

## Feeds
- [Three-layer architecture](../concepts/three-layer-architecture.md)
- [Andrej Karpathy](../entities/andrej-karpathy.md)
- [LLM Wiki vs traditional RAG](../summaries/llm-wiki-vs-rag.md)
