---
title: The LLM-wiki concept — an overview
type: summary
tags: [overview, llm-wiki, okf, start-here, compounding, rag]
status: stable
created: 2026-10-30
updated: 2026-10-30
sources: [source-karpathy-llm-wiki-gist, source-joshi-medium-llm-wiki, source-google-okf-blog, source-okf-spec]
generated: { by: claude-code/opus-4.8, at: 2026-10-30T00:00:00Z }
---

# The LLM-wiki concept — an overview

The front door to this wiki. In one sentence: **have an AI compile scattered
sources once into a persistent, structured, cross-linked knowledge base, and keep
it updated — instead of re-reading raw documents on every question.**

## At a glance

```mermaid
flowchart LR
    SRC["📄 Raw sources (immutable)<br/>links · PDFs · specs · talks"]
    LLM["🤖 LLM<br/>ingest · compile · lint"]

    subgraph BUNDLE["OKF / LLM-Wiki bundle — compounding"]
        direction TB
        KB(["📚 concepts · entities · summaries<br/>index.md · log.md"])
        TR["🔒 provenance · verified tier<br/>attested · stale_after"]
    end

    PL["🖥️ Presentation layer<br/>Obsidian · Astro · GitBook"]
    HUM["👥 Humans"]
    AG["🤝 Agents / AI"]
    APP["🧩 Applications<br/>AI-native SDLC · 1EdTech specs<br/>learning analytics"]

    SRC == "compile once" ==> LLM ==> BUNDLE ==> PL
    PL --> HUM
    PL == "MCP · llms.txt · EduQuery" ==> AG
    BUNDLE -. powers .-> APP

    classDef src fill:#f1f3f4,stroke:#9aa0a6,color:#111;
    classDef llm fill:#e8f0fe,stroke:#4285f4,color:#111;
    classDef bundle fill:#fef7e0,stroke:#fbbc04,color:#111;
    classDef pl fill:#e6f4ea,stroke:#34a853,color:#111;
    classDef human fill:#fde8f3,stroke:#c2508f,color:#111;
    classDef agent fill:#f1f3f4,stroke:#9aa0a6,color:#111;
    classDef app fill:#ede7f6,stroke:#7e57c2,color:#111;
    class SRC src; class LLM llm; class KB,TR bundle; class PL pl; class HUM human; class AG agent; class APP app;
```

## Why — compile, don't re-retrieve
Traditional RAG re-reads raw documents and rediscovers the same connections on every
query. The LLM-wiki pattern pays that cost **once**, at ingestion, and banks the
result as a durable page — so knowledge **compounds** instead of being rediscovered.
The analogy: raw sources are *source code*; the wiki is the *compiled binary*. See
[LLM Wiki vs traditional RAG](llm-wiki-vs-rag.md) and
[Knowledge as compilation](../concepts/knowledge-compilation-analogy.md).

## The three layers
1. **Raw sources** — immutable; read, never rewritten.
2. **The wiki** — LLM-generated `concepts/`, `entities/`, `summaries/` + `index.md` / `log.md`.
3. **The schema** — [`CLAUDE.md`](../CLAUDE.md): conventions + workflows.

See [Three-layer architecture](../concepts/three-layer-architecture.md).

## The three operations
- **Ingest** — read a source → summarize → touch ~10–15 pages.
- **Query** — read the synthesized wiki, not the raw docs; file good answers back.
- **Lint** — audit for contradictions, orphans, stale claims, broken links.

See [The three operations](../concepts/three-operations.md).

## Making it trustworthy
The pattern's headline risk is that a summary error gets
[baked in as a "fact"](../concepts/hallucination-baking-risk.md) and propagates. The
[Open Knowledge Format](../concepts/open-knowledge-format.md) (OKF) answers this with
machine-readable [provenance and trust](../concepts/provenance-and-trust.md) —
`generated`/`verified` tiers, `stale_after`, and
[Attested Computation](../concepts/attested-computation.md) for computed facts. A
community can tighten OKF into an [OKF profile](../concepts/okf-profile.md).

## Serving it to humans and agents
One bundle, a swappable [presentation layer](../concepts/presentation-layer.md)
(Obsidian / Astro / GitBook) for people, and agent endpoints
([MCP](../concepts/model-context-protocol.md), `llms.txt`, EduQuery) for machines —
"one architecture can serve humans and Agents alike."

## Where it applies
- **Software** — a compounding memory beside the [AI-native SDLC](llm-wiki-applied-to-sdlc.md).
- **Standards & data** — [OKF bundles of 1EdTech specs](okf-for-1edtech-specs.md) for
  unified semantics and conformance; the [context dictionary](../concepts/context-dictionary.md)
  that turns an interoperable "Completed" event into a teaching decision
  ([One Data, One Meaning](one-data-one-meaning.md)).

## Lineage
Vannevar Bush's 1945 [Memex](../concepts/memex.md) (associative trails, abandoned over
bookkeeping) → Karpathy's [LLM Wiki](../sources/source-karpathy-llm-wiki-gist.md)
(the LLM does the bookkeeping) → Google's [OKF](../entities/google-cloud-knowledge-catalog.md)
(an interoperable format) → applied to EdTech by [1EdTech](../entities/1edtech.md) and
in [this talk](one-data-one-meaning.md).

## This wiki is its own example
Everything above is maintained *as* an LLM-wiki/OKF bundle — the method describing
itself. Start exploring from [index.md](../index.md); the
[change log](../log.md) shows how it compounded.

## Sources
- [Karpathy — LLM Wiki gist](../sources/source-karpathy-llm-wiki-gist.md)
- [Joshi — LLM Wiki walkthrough](../sources/source-joshi-medium-llm-wiki.md)
- [Google Cloud — OKF blog](../sources/source-google-okf-blog.md)
- [OKF Specification v0.2](../sources/source-okf-spec.md)
