---
title: GitBook
type: entity
tags: [tool, docs, gitbook, git-sync, presentation, mcp, saas]
status: draft
created: 2026-09-25
updated: 2026-09-25
sources: [source-gitbook-docs]
---

# GitBook

A hosted documentation platform that can be backed by a Git repo of Markdown and
published as a searchable site. A concrete
[presentation layer](../concepts/presentation-layer.md) over an
[OKF bundle](../concepts/open-knowledge-format.md).

## What it contributes over a bundle
- **Bidirectional Git Sync** — "changes you make directly in GitBook's editor are
  automatically synced, as are any commits made on GitHub or GitLab," so the LLM
  maintains the repo while humans edit in GitBook.
- **Change requests + review** — a human sign-off gate that realises the
  [verified trust tier](../concepts/provenance-and-trust.md).
- **Human surface** — search, TOC, versioning, custom domains (Aracil's
  "[microsite](1edtech-ai-enablers.md)", as a product).
- **Agent surface** — a **GitBook MCP** server ("your published docs as a tool, so
  your customers' agents can read them properly"), an **`llms.txt`** index, and
  `.md` export — an access layer alongside [EduQuery](eduquery.md).

## The caveats
Frontmatter/metadata round-trip isn't guaranteed by the sync docs checked, and no
conflict-resolution priority is documented — so keep the **repo authoritative** for
OKF's trust/attestation metadata, and let GitBook render + host + review. It does not
*compile* or *attest*; that stays with the [LLM maintainer](../concepts/three-layer-architecture.md)
and CI in the repo.

## Sources
- [GitBook — product documentation](../sources/source-gitbook-docs.md)

## Related
- [Presentation layer](../concepts/presentation-layer.md) · [Astro](astro.md) · [Obsidian](obsidian.md)
