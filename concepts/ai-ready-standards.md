---
title: AI-ready standards
type: concept
tags: [standards, ai-ready, machine-readable, traceability, 1edtech]
status: draft
created: 2026-09-16
updated: 2026-09-16
sources: [source-aracil-standards-adoption]
---

# AI-ready standards

[Aracil's](../sources/source-aracil-standards-adoption.md) criteria for a standard
that AI can adopt reliably. The premise: new adopters will increasingly learn a
standard *through* AI, so the standard itself must be built for machine consumption —
not just published as prose.

## The three properties
1. **Structured content** — stable identifiers and clear relationships between
   concepts across the ecosystem.
2. **Machine-readable** — representations that let automated tools parse, validate,
   and reference requirements.
3. **Traceability** — connecting requirements ↔ implementation guidance ↔ tests ↔
   trusted source control.

Goal: a new adopter gets from "zero → working example within 60 mins."

## Why it's the OKF pattern by another name
These three map almost one-to-one onto an [OKF bundle](open-knowledge-format.md):
structured content = concept/entity pages with stable slugs; machine-readable =
markdown + YAML frontmatter a tool can parse; traceability = the `sources` provenance
family plus cross-links, and [attested conformance](attested-computation.md) tying
requirements to runnable tests. See
[Applying OKF to 1EdTech specs](../summaries/okf-for-1edtech-specs.md).

The distinguishing demand is **authority**: an AI-ready standard needs
*authoritative* retrieval and human sign-off, not just any structured text — which is
exactly the [verified trust tier](provenance-and-trust.md).

## Sources
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)

## Related
- [The standards-adoption journey](standards-adoption-journey.md) · [The unified-semantics gap](unified-semantics-gap.md)
- [Open Knowledge Format](open-knowledge-format.md)
