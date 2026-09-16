---
title: "1EdTech (Aracil) — The path to easier standards adoption"
type: source
tags: [edtech, 1edtech, standards, ai-ready, machine-readable, adoption, conformance]
status: stable
created: 2026-09-16
updated: 2026-09-16
url: "file: C:/Users/markm/Downloads/Day2 10.15 ARACIL The path to easier standards adoption - embrace new audiences.pdf"
author: Xavi Aracil (Technical Standards Architect, 1EdTech)
published: unknown
accessed: 2026-09-16
source_type: slides
link_status: live
---

# 1EdTech (Aracil) — The path to easier standards adoption: embracing new audiences

**A 1EdTech conference talk on making standards "AI-ready" — machine-readable, structured, and traceable — so new adopters learn and implement them through AI, with trusted (not just fast) answers.** _(Private local presentation, 23 slides.)_

## Summary
Aracil frames the standards-adoption journey — Discover → Understand → Implement →
Validate → Maintain — as friction at every step (dense specs across silos, human
interpretation barriers, verification friction, versioning complexity). AI now sits
in nearly every developer workflow and generates tests, payloads, and integration
code, which *lowers* the adoption curve but *raises* the risk of ambiguity, wrong
answers, inconsistent implementations, and interoperability issues. The thesis:
"Implementers need trusted answers, not just fast answers. Gen AI over unstructured
documents is not enough." The response is **AI-Ready standards** (structured content,
machine-readable, traceable) and a 1EdTech strategy of standards **microsites**,
**machine-readable specs (MR-Specs)**, and **future tooling** — with concrete AI
enablers already shipping (a Build Platform, a Model Processing Service that packages
**Skills** for specs, and a Standards Portal).

## Key claims / quotes
- Thesis: "Gen AI over unstructured documents is not enough" — need trusted, not
  just fast, answers. → [Hallucination-baking risk](../concepts/hallucination-baking-risk.md), [LLM Wiki vs RAG](../summaries/llm-wiki-vs-rag.md)
- The adoption journey has five friction points; "most implementers are not waking
  up hoping to cross-reference four documents and a GitHub issue." → [The standards-adoption journey](../concepts/standards-adoption-journey.md)
- **Standards MUST be machine-readable**; new adopters will learn standards through
  AI; goal: "zero → working example within 60 mins." → [AI-ready standards](../concepts/ai-ready-standards.md)
- **AI-Ready = Structured Content + Machine-Readable + Traceability** (stable
  identifiers, parse/validate/reference requirements, connect requirements ↔ guidance
  ↔ tests ↔ source control).
- **"Working for Both Claudes"**: the machine needs structure and authoritative
  retrieval; the human brings judgment — "Claude AI is faster at scanning, but Claude
  V is better at saying 'That is not what the workgroup meant.'" → [Provenance and trust](../concepts/provenance-and-trust.md)
- Strategy = **Microsites** (unified navigation, normative material separated from
  guidance, deep traceability) + **MR-Specs** (preserve meaning, not just format) +
  **Future Tooling**. Enablers: Build Platform, Model Processing Service (ships spec
  **Skills**), Standards Portal (standards.1edtech.org). → [1EdTech AI Enablers](../entities/1edtech-ai-enablers.md)
- Status matrix across LTI, QTI, Caliper, Open Badges/CLR, OneRoster/Edu-API, CASE,
  Common Cartridge.

## Why it matters here
This is direct evidence that a major standards body is **independently converging on
the LLM-wiki / OKF pattern**: machine-readable, structured, traceable specs consumed
by AI with human-authoritative review — the wiki's whole argument, arrived at from the
standards side. It reinforces and extends the
[OKF-for-1EdTech application](../summaries/okf-for-1edtech-specs.md) (the EduQuery
deck was the *query* side; this is the *authoring/adoption* side) and supplies a
crisp articulation of "trusted answers over unstructured RAG."

## Feeds
- [Applying OKF / the LLM wiki to 1EdTech specs](../summaries/okf-for-1edtech-specs.md)
- [AI-ready standards](../concepts/ai-ready-standards.md)
- [The standards-adoption journey](../concepts/standards-adoption-journey.md)
- [1EdTech AI Enablers](../entities/1edtech-ai-enablers.md) · [Xavi Aracil](../entities/xavi-aracil.md) · [1EdTech](../entities/1edtech.md)
