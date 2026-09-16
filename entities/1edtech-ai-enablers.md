---
title: 1EdTech AI Enablers
type: entity
tags: [tool, 1edtech, program, machine-readable, skills, portal, mps]
status: draft
created: 2026-09-16
updated: 2026-09-16
sources: [source-aracil-standards-adoption]
---

# 1EdTech AI Enablers

The concrete program [1EdTech](1edtech.md) is building (per
[Aracil](../sources/source-aracil-standards-adoption.md)) to make its standards
[AI-ready](../concepts/ai-ready-standards.md). Notable because it is a real standards
body shipping the [LLM-wiki / OKF](../concepts/open-knowledge-format.md) pattern.

## The pieces
- **Standards Microsites** — a unified navigation/accessibility layer that separates
  core normative material from surrounding guidance while keeping deep traceability
  ("a better standards experience is the goal").
- **MR-Specs (machine-readable specifications)** — not just format conversion but
  *preserving meaning* and logical relationships, enabling generated documentation,
  implementation checklists, test alignment, and conformance workflows. This is the
  OKF-bundle idea in 1EdTech's own words.
- **Model Processing Service (MPS)** — packages developer artifacts, data models, and
  **Skills** for specs. Its skills carry activation triggers and instructions for an
  agent (e.g. an "Edu-API 1.0 Skill") — directly analogous to Claude Code Skills.
- **Build Platform** — generates tests, certs, and models.
- **Standards Portal** — `standards.1edtech.org`; search and jump from tools to docs,
  with embedded links to dev tools/tests.

Status is tracked per spec (LTI, QTI, Caliper, Open Badges/CLR, OneRoster/Edu-API,
CASE, Common Cartridge) across MPS / Build Portal / Standards Portal.

## Relevance to this wiki
The MR-Specs are effectively an [OKF bundle of specs](../summaries/okf-for-1edtech-specs.md);
the microsites are its navigation layer (an `index.md` for humans); the MPS Skills are
the agent-facing instructions; and the conformance workflows are
[attested computation](../concepts/attested-computation.md) in practice.

## Sources
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)

## Related
- [EduQuery](eduquery.md) · [AI-ready standards](../concepts/ai-ready-standards.md)
