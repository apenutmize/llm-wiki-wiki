---
title: "Joshi — Andrej Karpathy's LLM Wiki: Create your own knowledge base"
type: source
tags: [llm-wiki, rag, memex, obsidian, tutorial, knowledge-base]
status: stable
created: 2026-09-02
updated: 2026-09-02
url: https://medium.com/@urvvil08/andrej-karpathys-llm-wiki-create-your-own-knowledge-base-8779014accd5
author: Urvil Joshi
published: 2026-04-20
accessed: 2026-09-02
source_type: blog
link_status: live
---

# Joshi — Andrej Karpathy's LLM Wiki: Create your own knowledge base   ·   [Medium](https://medium.com/@urvvil08/andrej-karpathys-llm-wiki-create-your-own-knowledge-base-8779014accd5)

**A ~9-minute walkthrough that explains Karpathy's LLM-wiki gist and builds a working example step by step, adding the compilation analogy, the Memex lineage, and an honest RAG comparison.**

## Summary
Joshi traces the pattern to a Karpathy tweet (Apr 2, 2026) followed by the
`llm-wiki.md` gist, framing the gist as an "idea file" you paste into an agent
(Claude Code, Codex, etc.) so it instantiates the pattern for you. The article
restates the three-layer architecture and reframes the three operations as
**ingest / query / lint**. It then walks through building a vault with Obsidian as
the viewer, ingesting two essays (Sutton's *Bitter Lesson*, Karpathy's *Software
2.0*) and showing how the second ingestion *densifies* the wiki by adding
backlinks the model infers. It closes with a candid RAG-vs-wiki comparison and the
Memex framing.

## Key claims / quotes
- Karpathy's compilation analogy: raw sources are source code, the wiki is the
  compiled binary — compile once, run (query) cheaply forever. → [Knowledge as compilation](../concepts/knowledge-compilation-analogy.md)
- Karpathy (quoted): "Obsidian is the IDE; the LLM is the programmer; the wiki is
  the codebase." → [Obsidian](../entities/obsidian.md)
- Three operations named **ingest / query / lint**; a single source can touch
  ~10–15 wiki pages. → [The three operations](../concepts/three-operations.md)
- The real cost/benefit is corpus-shaped: RAG suits large, changing corpora with
  precise citations; the wiki suits ~100–500 curated sources where synthesis
  matters. → [LLM Wiki vs traditional RAG](../summaries/llm-wiki-vs-rag.md)
- Named risk: summarization can **bake hallucinations in as "facts"** that
  propagate across linked pages — the reason the lint step matters. → [Hallucination-baking risk](../concepts/hallucination-baking-risk.md)
- Lineage: the pattern realizes Vannevar Bush's 1945 **Memex** — associative
  trails between curated documents; abandoned historically because of the
  bookkeeping burden, which LLMs now absorb. → [Memex](../concepts/memex.md)

## Why it matters here
This is the first *secondary* source in the wiki — it interprets and extends the
gist rather than originating the idea. It contributes several new concept pages
(compilation analogy, three operations, hallucination risk, Memex) and enriches
the RAG comparison with specifics (traceability, corpus size, freshness,
hallucination locality). It also introduces the practical tooling layer (Obsidian).

## Feeds
- [Knowledge as compilation](../concepts/knowledge-compilation-analogy.md)
- [The three operations](../concepts/three-operations.md)
- [Hallucination-baking risk](../concepts/hallucination-baking-risk.md)
- [Memex](../concepts/memex.md)
- [LLM Wiki vs traditional RAG](../summaries/llm-wiki-vs-rag.md)
- [Three-layer architecture](../concepts/three-layer-architecture.md)
- [Urvil Joshi](../entities/urvil-joshi.md) · [Andrej Karpathy](../entities/andrej-karpathy.md) · [Vannevar Bush](../entities/vannevar-bush.md) · [Obsidian](../entities/obsidian.md)
