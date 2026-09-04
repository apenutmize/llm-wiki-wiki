---
title: Open Knowledge Format (OKF)
type: concept
tags: [okf, standard, llm-wiki, markdown, yaml, interoperability]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-google-okf-blog, source-okf-spec]
---

# Open Knowledge Format (OKF)

**OKF is an open, vendor-neutral specification that formalizes the LLM-wiki
pattern into a portable, interoperable format.** Published by Google Cloud
(spec v0.2 in the `knowledge-catalog` repo), it turns "a directory of markdown the
LLM maintains" from a personal convention into a shared standard.

## What it is
- A **format, not a platform**: plain markdown files with YAML frontmatter, shipped
  as a git repo, tarball, or subdirectory. No SDK, runtime, or proprietary account.
- **Minimally opinionated**: the only mandatory field is `type`; everything else is
  optional, and consumers must tolerate missing fields, unknown types, and broken
  links.
- Portability premise (spec): "If you can `cat` a file, you can read OKF."

## Relationship to the LLM-wiki pattern
OKF is the LLM-wiki pattern's [wiki layer](three-layer-architecture.md)
standardized. It shares the same primitives this wiki uses — markdown + YAML
frontmatter, an `index.md` catalog, a `log.md` history, concepts as files, sources
as provenance, a `status` lifecycle. The difference is scope: Karpathy's gist is a
*personal* pattern; OKF makes bundles **exchangeable between organizations and
tools**. See [OKF vs this wiki's schema](../summaries/okf-vs-this-wiki-schema.md).

## What it adds beyond the gist
- **Producer/consumer independence** — the knowledge format is decoupled from the
  tools that consume it, so any agent or catalog can read the same bundle.
- **[Provenance, trust, and attestation](provenance-and-trust.md)** — machine-
  readable credibility signals that directly target the
  [hallucination-baking risk](hallucination-baking-risk.md).
- **[Attested Computation](attested-computation.md)** — a way to bless and verify
  how a value was computed, not just assert it.

## Why it matters
It's evidence the LLM-wiki idea is being adopted as industry infrastructure, and it
supplies the reliability machinery the raw pattern lacked. "The format itself is
the contribution" — positioned as a lingua franca for exchanging knowledge.

## Sources
- [Google Cloud — OKF blog](../sources/source-google-okf-blog.md)
- [OKF Specification v0.2](../sources/source-okf-spec.md)

## Applications
- [Applying OKF to the AI-native SDLC](../summaries/llm-wiki-applied-to-sdlc.md) — knowledge layer for a software pipeline.
- [Applying OKF to 1EdTech specs](../summaries/okf-for-1edtech-specs.md) — a spec bundle for unified semantics and conformance assurance behind EduQuery.

## Related
- [Knowledge Bundle](knowledge-bundle.md) · [The context-assembly problem](context-assembly-problem.md)
- [Google Cloud Knowledge Catalog](../entities/google-cloud-knowledge-catalog.md)
