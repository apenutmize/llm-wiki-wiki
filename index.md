---
okf_version: "0.2"
title: Index
---

# Index

Catalog of every page, grouped by category. Kept in sync on each ingestion and
page creation. See [CLAUDE.md](CLAUDE.md) for the schema.

## Concepts
- [Three-layer architecture](concepts/three-layer-architecture.md) — raw sources / wiki / schema layering, and why the separation matters.
- [The three operations](concepts/three-operations.md) — ingest / query / lint, and how each compounds the wiki.
- [Knowledge as compilation](concepts/knowledge-compilation-analogy.md) — raw sources are source code; the wiki is the compiled binary.
- [Hallucination-baking risk](concepts/hallucination-baking-risk.md) — how a summarization error can propagate across linked pages, and how OKF guards against it.
- [Memex](concepts/memex.md) — Vannevar Bush's 1945 vision the pattern finally makes practical.
- [Open Knowledge Format (OKF)](concepts/open-knowledge-format.md) — Google's open spec that formalizes the LLM-wiki pattern.
- [Knowledge Bundle](concepts/knowledge-bundle.md) — OKF's packaging unit: a directory of markdown concepts with reserved index/log files.
- [Provenance and trust](concepts/provenance-and-trust.md) — OKF's machine-readable credibility signals and trust tiers.
- [Attested Computation](concepts/attested-computation.md) — OKF's verifiable contract for computed values.
- [The context-assembly problem](concepts/context-assembly-problem.md) — the fragmentation OKF is pitched to solve.
- [Flow-through vs compounding artifacts](concepts/flow-through-vs-compounding-artifacts.md) — why a pipeline of Markdown files isn't yet a compounding wiki.

## Entities
- [Andrej Karpathy](entities/andrej-karpathy.md) — originator of the LLM-wiki framing.
- [Urvil Joshi](entities/urvil-joshi.md) — author of the walkthrough that extends the gist.
- [Vannevar Bush](entities/vannevar-bush.md) — originator of the Memex concept.
- [Obsidian](entities/obsidian.md) — the Markdown viewer / graph view over the vault.
- [Sam McVeety](entities/sam-mcveety.md) — Google Cloud; co-author of the OKF announcement.
- [Amir Hormati](entities/amir-hormati.md) — Google Cloud BigQuery; co-author of the OKF announcement.
- [Google Cloud Knowledge Catalog](entities/google-cloud-knowledge-catalog.md) — OKF's reference host and consumer.
- [Anthropic](entities/anthropic.md) — maker of Claude Code / CLAUDE.md; author of the AI-native SDLC playbook.

## Summaries
- [LLM Wiki vs traditional RAG](summaries/llm-wiki-vs-rag.md) — why compounding beats re-retrieval, and where RAG still wins.
- [OKF vs this wiki's schema](summaries/okf-vs-this-wiki-schema.md) — how the open standard compares to this wiki's own CLAUDE.md conventions.
- [Applying the LLM wiki to the AI-native SDLC](summaries/llm-wiki-applied-to-sdlc.md) — adding a compounding memory layer to Anthropic's six-stage pipeline.

## Sources
- [Karpathy — LLM Wiki gist](sources/source-karpathy-llm-wiki-gist.md) — the seed idea. (live)
- [Joshi — LLM Wiki walkthrough](sources/source-joshi-medium-llm-wiki.md) — Medium tutorial extending the gist. (live)
- [Google Cloud — OKF blog](sources/source-google-okf-blog.md) — announcement of the Open Knowledge Format. (live)
- [OKF Specification v0.2](sources/source-okf-spec.md) — the normative spec in the knowledge-catalog repo. (live)
- [Anthropic — AI-Native SDLC Playbook](sources/source-anthropic-ai-native-sdlc.md) — a real-world application of the pattern to the software lifecycle. (live)
