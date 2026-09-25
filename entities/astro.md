---
title: Astro
type: entity
tags: [tool, static-site-generator, astro, presentation, markdown, 1edtech]
status: draft
created: 2026-09-25
updated: 2026-09-25
sources: [source-aracil-standards-adoption]
---

# Astro

An open-source static-site generator built around content (Markdown/MDX), with
**content collections** that validate frontmatter against a declared schema. A
self-built [presentation layer](../concepts/presentation-layer.md) over an
[OKF bundle](../concepts/open-knowledge-format.md).

## Why it fits the pattern
- Renders a repo of Markdown + YAML frontmatter directly into a fast static site —
  no SaaS, fully self-hosted, the repo stays the source of truth.
- Its schema-validated content collections line up naturally with an
  [OKF profile](../concepts/okf-profile.md): the same frontmatter that types the
  bundle can be validated and used to drive the site (badges for
  [trust tier](../concepts/provenance-and-trust.md), stale warnings, provenance links).
- Per the wiki maintainer, **1EdTech's standards [microsites](1edtech-ai-enablers.md)
  are built on Astro** — making Astro the concrete engine behind Aracil's microsite
  strategy.

## GitBook vs Astro vs Obsidian
Three points on one spectrum: [Obsidian](obsidian.md) (local editor/viewer),
**Astro** (self-built, self-hosted static site), [GitBook](gitbook.md) (hosted SaaS
with editing + review). All render the same bundle; they differ in hosting, editing,
and how much comes out of the box.

## Sources
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md) (microsites); Astro detail per the maintainer.

## Related
- [Presentation layer](../concepts/presentation-layer.md) · [1EdTech AI Enablers](1edtech-ai-enablers.md)

_Stub._
