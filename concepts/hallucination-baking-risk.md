---
title: Hallucination-baking risk
type: concept
tags: [llm-wiki, risk, reliability, critique]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-joshi-medium-llm-wiki, source-okf-spec]
---

# Hallucination-baking risk

The most serious critique of the LLM-wiki pattern: because the model **summarizes
and compresses** sources into wiki pages, a mistake can get baked in as a "fact"
and then **propagate across linked pages**.

## The contrast with RAG
- In pure RAG, a wrong answer is **local** — one bad answer to one query, and the
  raw chunk is right there to check against.
- In an LLM wiki, a small misunderstanding written into a page can quietly spread
  as other pages cross-link to it, compounding the same way correct knowledge does.
See [LLM Wiki vs traditional RAG](../summaries/llm-wiki-vs-rag.md).

## Mitigations
- **Lint regularly** — the maintenance pass exists partly to catch this. See
  [The three operations](three-operations.md).
- **Spot-check generated pages against raw sources.** Because raw sources are
  [immutable](three-layer-architecture.md), the ground truth is always available to
  verify against.
- **Keep provenance tight** — every claim on a synthesis page should trace to a
  source note, so a suspect claim can be traced back and corrected.

## How OKF hardens against it
The [Open Knowledge Format](open-knowledge-format.md) turns these mitigations from
good habits into machine-checkable structure:
- **[Trust tiers](provenance-and-trust.md)** — `verified` metadata lets a consumer
  distinguish unverified from machine-confirmed from human-reviewed pages, and gate
  on it.
- **Staleness** — `stale_after` makes "is this claim still current?" a check, not a
  guess.
- **[Attested Computation](attested-computation.md)** — computed values can be
  re-executed and verified rather than trusted, so a fabricated number fails the gate.

## Why it's a design concern, not a dealbreaker
The pattern deliberately trades a step of source-traceability (answers are 1–2
steps removed from raw text) for cross-source synthesis. That trade-off is
acceptable for a bounded, curated corpus you actively maintain — and unacceptable
for high-stakes, fast-changing corpora, which is RAG's territory.

## Sources
- [Joshi — LLM Wiki walkthrough](../sources/source-joshi-medium-llm-wiki.md)
- [OKF Specification v0.2](../sources/source-okf-spec.md)
