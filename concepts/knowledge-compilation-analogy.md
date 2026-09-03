---
title: Knowledge as compilation
type: concept
tags: [llm-wiki, analogy, mental-model]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-joshi-medium-llm-wiki]
---

# Knowledge as compilation

The mental model that makes the LLM-wiki pattern click: **treat knowledge the way
software treats source code.**

## The analogy
- **Source code → binary.** You don't re-run source every time you want the
  program; you compile it once and execute the fast binary repeatedly.
- **Raw sources → wiki.** Your PDFs, notes, and articles are the source code. The
  wiki is the compiled binary: pre-synthesized, interlinked, ready to "run" (query)
  cheaply every time.

Compilation happens at **ingestion**: the model reads a source, extracts key
information, updates existing pages, revises summaries, flags contradictions, and
strengthens cross-links. Query time then just "runs the binary" — reading
already-synthesized pages instead of reprocessing raw documents.

## Why it's useful
- It explains *where the cost goes*: front-loaded at ingest, cheap per query — the
  inverse of stateless RAG. See [LLM Wiki vs traditional RAG](../summaries/llm-wiki-vs-rag.md).
- It justifies keeping raw sources **immutable**: like source code, you can always
  re-compile the wiki from scratch. See [Three-layer architecture](../concepts/three-layer-architecture.md).

## Companion framing
For the *roles* in this analogy, Karpathy (as quoted by Joshi) puts it as:
"Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase." — you
curate and ask; the model writes and maintains. See [Obsidian](../entities/obsidian.md).

## Sources
- [Joshi — LLM Wiki walkthrough](../sources/source-joshi-medium-llm-wiki.md)
