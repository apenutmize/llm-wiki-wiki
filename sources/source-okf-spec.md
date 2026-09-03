---
title: "Open Knowledge Format (OKF) Specification, v0.2"
type: source
tags: [okf, spec, standard, markdown, yaml, provenance, attestation]
status: stable
created: 2026-09-02
updated: 2026-09-02
url: https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md
author: Google Cloud Platform (knowledge-catalog repo)
published: unknown
accessed: 2026-09-02
source_type: repo
link_status: live
---

# Open Knowledge Format (OKF) Specification, v0.2   ·   [SPEC.md](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)

**The normative spec: how OKF represents knowledge as plain markdown + YAML frontmatter, plus its provenance, trust, lifecycle, and attestation model.**

## Summary
OKF defines a **Knowledge Bundle** — a hierarchical directory of markdown files
shipped as a git repo, tarball, or subdirectory. Reserved files `index.md`
(progressive-disclosure listing) and `log.md` (chronological history) carry special
meaning; every other `.md` file is a **Concept**. A concept is YAML frontmatter
plus a structural-markdown body. The only mandatory field is `type`; everything
else is optional and consumers must tolerate missing fields, unknown types, unknown
keys, and broken links. Design goals: readable without tools, parseable without an
SDK, diffable in git, portable across orgs and time.

## Key claims / quotes
- Portability premise: "If you can `cat` a file, you can read OKF." →
  [Open Knowledge Format](../concepts/open-knowledge-format.md)
- Bundle = directory of markdown; `index.md` + `log.md` reserved; all other `.md`
  are Concepts. → [Knowledge Bundle](../concepts/knowledge-bundle.md)
- **Five frontmatter families**: provenance (`sources`), trust
  (`generated`/`verified`), lifecycle (`status`/`stale_after`), cross-linking
  (plain markdown links), attestation (`Attested Computation`). →
  [Provenance and trust](../concepts/provenance-and-trust.md)
- **Trust tiers** derived by consumers: unverified → machine-confirmed →
  human-reviewed (via a `human:` actor prefix).
- **Attested Computation**: a concept type encoding sanctioned computation so a
  consumer can verify a value came from a blessed procedure, not improvised SQL. →
  [Attested Computation](../concepts/attested-computation.md)
- Actor convention: `<producer>/<version>`, `human:<id>`, `process:<id>`.
- Conformance (§11): parseable frontmatter + non-empty `type` on every non-reserved
  file; reserved files follow their structures. Versioning is `<major>.<minor>`;
  bundles may declare `okf_version: "0.2"` in the root `index.md`.
- v0.1→v0.2 breaking changes: `timestamp` → `generated:{by,at}`; `# Citations`
  body section → `sources` frontmatter.

## Why it matters here
This is the primary, normative artifact behind the OKF blog post. It shows exactly
how the LLM-wiki pattern gets pinned down into machine-checkable conventions — and
its provenance/trust/attestation machinery is the concrete answer to the
[hallucination-baking risk](../concepts/hallucination-baking-risk.md). It also
parallels this wiki's own `CLAUDE.md` schema closely enough to compare directly.

## Feeds
- [Open Knowledge Format](../concepts/open-knowledge-format.md)
- [Knowledge Bundle](../concepts/knowledge-bundle.md)
- [Provenance and trust](../concepts/provenance-and-trust.md)
- [Attested Computation](../concepts/attested-computation.md)
- [OKF vs this wiki's schema](../summaries/okf-vs-this-wiki-schema.md)
- [Hallucination-baking risk](../concepts/hallucination-baking-risk.md)
