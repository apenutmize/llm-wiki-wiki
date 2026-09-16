---
title: LLM Wiki vs traditional RAG
type: summary
tags: [llm-wiki, rag, comparison, memory]
status: draft
created: 2026-09-02
updated: 2026-09-16
sources: [source-karpathy-llm-wiki-gist, source-joshi-medium-llm-wiki, source-aracil-standards-adoption]
---

# LLM Wiki vs traditional RAG

The central thesis of this wiki: a persistent, LLM-maintained wiki is an
alternative to traditional RAG that **compounds** knowledge instead of
**re-retrieving** it.

## The contrast

| | Traditional RAG | LLM Wiki |
|---|---|---|
| Per-query work | Retrieve raw docs, re-synthesize connections each time | Read an already-synthesized page |
| Cross-document links | Rediscovered on every query | Accumulated once, reused forever |
| Contradictions | Surface repeatedly, unresolved | Recorded and reconciled on pages |
| Artifact | Ephemeral (the answer) | Persistent, compounding wiki |
| State | Stateless — each query starts from scratch | Stateful — knowledge compounds over time |
| Cost trend | Cheap per query, no ingest cost | Expensive ingest, cheap query |
| Traceability | Precise — answer maps to an exact chunk | Answers sit 1–2 steps removed from raw source |
| Cross-time synthesis | None — no linking across documents | Naturally links an old source to a new one |
| Freshness | Always re-reads current data | Updates require re-ingesting the source |
| Error blast radius | Hallucination stays local to one answer | Can [bake in as a "fact"](../concepts/hallucination-baking-risk.md) and propagate |
| Best for | Large, changing corpora; fact lookup; millions of docs | ~100–500 curated sources; research; personal knowledge |

## Why it matters
In RAG, the model must rediscover the same connections across documents every time
a related question is asked. The LLM-wiki pattern pays that cost **once**, at
ingestion, and banks the result as a durable page. Over time the wiki grows richer
with each source and each query, whereas a pure-RAG system starts from raw
documents again and again.

The trade-off is up-front effort and maintenance: pages can go stale, contradict
each other, or orphan — which is why [maintenance](../CLAUDE.md) is a first-class
operation, not an afterthought.

## Neither wins — they solve different problems
Joshi's honest framing: RAG is best for large, constantly-changing corpora where
you need a precise citation to an exact chunk (support, legal search, enterprise
fact lookup). The LLM wiki is best for a **bounded, curated corpus** — a few
hundred sources on a topic you're going deep on — where the valuable answer
requires connecting five sources, not looking up one. The wiki's headline risk is
that summarization can [bake hallucinations in as facts](../concepts/hallucination-baking-risk.md)
that propagate; RAG keeps such errors local.

## Echoed from the standards world
1EdTech's [Aracil](../sources/source-aracil-standards-adoption.md) reaches the same
conclusion for standards adoption: "Gen AI over unstructured documents is not enough"
— implementers need *trusted* answers, not just fast ones. That is precisely the
compounding-wiki case: structure and attestation up front, so retrieval isn't
re-deriving (and re-risking) meaning on every query.

## Sources
- [Karpathy — LLM Wiki gist](../sources/source-karpathy-llm-wiki-gist.md)
- [Joshi — LLM Wiki walkthrough](../sources/source-joshi-medium-llm-wiki.md)
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)

## Related
- [Three-layer architecture](../concepts/three-layer-architecture.md)
- [Knowledge as compilation](../concepts/knowledge-compilation-analogy.md)
- [Hallucination-baking risk](../concepts/hallucination-baking-risk.md)
