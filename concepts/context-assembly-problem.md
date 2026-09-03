---
title: The context-assembly problem
type: concept
tags: [okf, agents, context, problem, fragmentation]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-google-okf-blog]
---

# The context-assembly problem

The problem [OKF](open-knowledge-format.md) is pitched to solve, and a useful
framing of *why* a shared knowledge format matters.

## The problem
Organizational knowledge is scattered across incompatible systems — metadata
catalogs, wikis, code comments, and "senior engineers' heads." To answer a
question, an AI agent must reassemble context from all of these every time. The
article's framing: "Every agent builder is solving the same context-assembly
problem from scratch," every catalog vendor reinvents the same data models, and the
knowledge stays locked behind whichever surface created it.

## Why it connects to the LLM wiki
- The [LLM-wiki pattern](three-layer-architecture.md) already answers the *per-user*
  version of this: compile scattered sources into one synthesized, interlinked wiki
  so you don't reassemble on every query.
- OKF generalizes that answer to the *cross-organization* version: if everyone's
  wiki speaks the same format, knowledge becomes portable instead of trapped —
  agents read and update **shared** markdown libraries that grow more useful over
  time.

## Sources
- [Google Cloud — OKF blog](../sources/source-google-okf-blog.md)

## Related
- [Open Knowledge Format](open-knowledge-format.md) · [Knowledge as compilation](knowledge-compilation-analogy.md)
