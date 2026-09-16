---
title: Provenance and trust
type: concept
tags: [okf, provenance, trust, verification, reliability]
status: draft
created: 2026-09-02
updated: 2026-09-16
sources: [source-okf-spec, source-aracil-standards-adoption]
---

# Provenance and trust

[OKF](open-knowledge-format.md)'s machine-readable answer to "can I believe this
page?" — the part of the spec that most directly addresses the
[hallucination-baking risk](hallucination-baking-risk.md). Of OKF's five
frontmatter families, three are about credibility.

## Provenance (`sources`)
Records the materials a concept derives from, capturing **objective** signals
(author, `usage_count`, `last_modified`, a `usage_window`) rather than subjective
scores. Per-claim attribution uses markdown **footnotes keyed to source IDs**, which
survive document rewrites better than positional indexing.

## Trust (`generated`, `verified`)
- `generated: { by, at }` records who/what created the content.
- `verified: [{ by, at }, ...]` records independent confirmations (multiple allowed).
- Consumers derive **trust tiers**:
  - no `verified` → **unverified**
  - verified by a non-human actor → **machine-confirmed**
  - verified by a human → **human-reviewed**
- **Actor convention**: `<producer>/<version>` for agents/tools, `human:<id>` for
  people, `process:<id>` for workflows. The `human:` prefix is what promotes a page
  to the human-reviewed tier.

## Lifecycle (`status`, `stale_after`)
- `status`: `draft | stable | deprecated` (default `stable`).
- `stale_after`: an absolute ISO-8601 instant; content is stale once the current
  time reaches it. This makes the "stale claims" maintenance check machine-checkable.

## Why it matters here
This is the reliability layer the raw LLM-wiki pattern lacked. Where the
[hallucination-baking risk](hallucination-baking-risk.md) warns that summarization
errors can propagate, OKF lets a consumer *gate* on trust tier and staleness — and,
for computed values, on [attestation](attested-computation.md).

## "Working for Both Claudes"
Aracil's [standards-adoption talk](../sources/source-aracil-standards-adoption.md)
frames the same split memorably: the machine ("Claude AI") needs structure, stable
references, and authoritative retrieval; the human ("Claude V") brings judgment —
"faster at scanning, but Claude V is better at saying 'that is not what the workgroup
meant.'" That human authority is exactly what promotes a page to the **human-reviewed**
tier; machine-generated content stays provisional until a person signs off.

## Sources
- [OKF Specification v0.2](../sources/source-okf-spec.md)
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)

## Related
- [Attested Computation](attested-computation.md) · [Knowledge Bundle](knowledge-bundle.md)
- [AI-ready standards](ai-ready-standards.md)
