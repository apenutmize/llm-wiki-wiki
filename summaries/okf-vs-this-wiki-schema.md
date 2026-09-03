---
title: OKF vs this wiki's schema
type: summary
tags: [okf, schema, comparison, meta, claude-md]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-okf-spec, source-karpathy-llm-wiki-gist]
generated: { by: claude-code/opus-4.8, at: 2026-09-02T00:00:00Z }
---

# OKF vs this wiki's schema

A meta observation: this wiki's own [CLAUDE.md](../CLAUDE.md) schema and
[OKF](../concepts/open-knowledge-format.md) independently converge on almost the
same primitives — both descend from the same [LLM-wiki pattern](../concepts/three-layer-architecture.md).
Where they differ is instructive.

## Where they agree
| Primitive | This wiki (CLAUDE.md) | OKF v0.2 |
|---|---|---|
| Storage | Markdown files with YAML frontmatter | Markdown files with YAML frontmatter |
| Catalog | `index.md` | `index.md` (reserved, progressive disclosure) |
| History | `log.md` (append-only) | `log.md` (reserved, chronological) |
| Unit | concept / entity / summary / source pages | Concept files (`type` defines the kind) |
| Provenance | `sources:` front matter + inline links | `sources:` family + footnote-keyed claims |
| Lifecycle | `status: stub/draft/stable` | `status: draft/stable/deprecated`, `stale_after` |
| Linking | relative markdown links | markdown links (bundle-relative preferred) |

## Where OKF goes further
- **Fixed conformance rules** — a bundle formally conforms if every non-reserved
  file has parseable frontmatter with a non-empty `type`. Our schema is convention,
  not a validator.
- **Machine-readable trust** — `generated`/`verified` yield unverified →
  machine-confirmed → human-reviewed tiers; we track maturity only informally. See
  [Provenance and trust](../concepts/provenance-and-trust.md).
- **[Attested Computation](../concepts/attested-computation.md)** — a verifiable
  contract for computed values; nothing in our schema covers this.
- **Open typing** — producers invent their own `type`s with no registry; we use a
  small fixed set (concept/entity/summary/source).

## Where this wiki is (deliberately) simpler
- A closed, human-curated set of page types keeps a small link-centric wiki legible.
- No attestation or trust tiers — appropriate for a reference wiki of curated
  links rather than agent-consumed data with computed values.

## Takeaway
OKF is essentially "our schema, hardened for interoperability and machine
consumption." If this wiki ever needed to be **exchanged** or **fed to agents**,
adopting OKF conventions (conformance, trust families, attestation) would be the
upgrade path. For a personal link wiki, the lighter `CLAUDE.md` conventions suffice.

## Sources
- [OKF Specification v0.2](../sources/source-okf-spec.md)
- [Karpathy — LLM Wiki gist](../sources/source-karpathy-llm-wiki-gist.md)

## Related
- [Open Knowledge Format](../concepts/open-knowledge-format.md) · [Knowledge Bundle](../concepts/knowledge-bundle.md)
