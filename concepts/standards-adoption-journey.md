---
title: The standards-adoption journey
type: concept
tags: [standards, adoption, lifecycle, 1edtech, friction]
status: draft
created: 2026-09-16
updated: 2026-09-16
sources: [source-aracil-standards-adoption]
---

# The standards-adoption journey

[Aracil's](../sources/source-aracil-standards-adoption.md) five-stage model of how an
implementer adopts a standard — and the friction at each stage that AI-ready,
knowledge-based tooling is meant to remove.

## The five stages (and their friction)
1. **Discover** — "where is the right document?" Dense specs spread across silos.
2. **Understand** — "what does this requirement mean?" Human-interpretation barriers.
3. **Implement** — "what examples can I trust?" Missing normative context.
4. **Validate** — "did I implement correctly?" Verification friction.
5. **Maintain** — "what changed in the new version?" Versioning complexity.

"Most implementers are not waking up hoping to cross-reference four documents and a
GitHub issue."

## Mapping to the LLM-wiki operations
The journey is the same shape as the wiki's [three operations](three-operations.md),
seen from the adopter's side:
- Discover + Understand → **query** a knowledge bundle instead of hunting silos.
- Implement + Validate → **attested** examples and [conformance checks](attested-computation.md)
  supply *trusted* normative context, not just retrieved text.
- Maintain → **lint** against `stale_after` when a new spec version ships.

This is why "Gen AI over unstructured documents is not enough" — retrieval eases
Discover but leaves Understand/Validate/Maintain unsolved. A compounding, attested
knowledge layer addresses all five. See [Hallucination-baking risk](hallucination-baking-risk.md).

## Sources
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)

## Related
- [AI-ready standards](ai-ready-standards.md) · [The three operations](three-operations.md)
- [Applying OKF to 1EdTech specs](../summaries/okf-for-1edtech-specs.md)
