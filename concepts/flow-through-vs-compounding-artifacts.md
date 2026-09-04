---
title: Flow-through vs compounding artifacts
type: concept
tags: [pattern, artifacts, sdlc, compounding, distinction]
status: draft
created: 2026-09-04
updated: 2026-09-04
sources: [source-anthropic-ai-native-sdlc, source-karpathy-llm-wiki-gist]
---

# Flow-through vs compounding artifacts

A distinction that clarifies where the LLM-wiki pattern fits alongside other
Markdown-driven agent workflows: not every versioned Markdown file is a wiki.

## The two kinds
- **Flow-through artifacts** are scoped to one unit of work and consumed as they
  move through a process. In the [AI-native SDLC](../summaries/llm-wiki-applied-to-sdlc.md),
  `intent.md` → `spec.md` → `plan.md` flow through the stages of a single feature,
  then are archived. Their value is spent when the feature ships.
- **Compounding artifacts** persist and accumulate. The [wiki layer](three-layer-architecture.md)
  gets *richer* with every source: cross-references, contradictions, and synthesis
  build up over time. Karpathy's framing calls this a "persistent, compounding
  artifact."

## Why the distinction matters
The same substrate (Markdown + YAML frontmatter, `CLAUDE.md`) can carry both — so
it's easy to assume a pipeline full of flow-through artifacts already *is* a
knowledge base. It isn't. Knowledge only compounds if something **ingests** the
flow-through artifacts into a persistent layer and synthesizes across them. In the
[compilation analogy](knowledge-compilation-analogy.md): flow-through artifacts are
the source code of a single build; the compounding wiki is the binary that
accumulates across builds.

## Sources
- [Anthropic — AI-Native SDLC Playbook](../sources/source-anthropic-ai-native-sdlc.md)
- [Karpathy — LLM Wiki gist](../sources/source-karpathy-llm-wiki-gist.md)

## Related
- [Applying the LLM wiki to the AI-native SDLC](../summaries/llm-wiki-applied-to-sdlc.md)
- [Knowledge as compilation](knowledge-compilation-analogy.md)
