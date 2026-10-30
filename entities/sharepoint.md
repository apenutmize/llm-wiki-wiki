---
title: SharePoint
type: entity
tags: [tool, microsoft, m365, sharepoint, presentation, storage, enterprise, governance]
status: draft
created: 2026-10-30
updated: 2026-10-30
sources: []
generated: { by: claude-code/opus-4.8, at: 2026-10-30T00:00:00Z }
---

# SharePoint

Microsoft 365's document/content platform. Relevant to the LLM-wiki pattern in three
roles at once — and notable for keeping everything inside an enterprise
governance/data-residency boundary (which matters for schools and publishers).

> _Analysis, not an ingested source — `generated`/unverified. Verify feature
> specifics (Graph API, content types, approval flows, Copilot/Graph connectors)
> against current Microsoft documentation before relying on them._

## Three roles
1. **Raw-source corpus (ingest from it).** SharePoint is usually where sprawling
   org docs already live; the [LLM maintainer](../concepts/three-layer-architecture.md)
   reads them via the **Microsoft Graph API** and compiles them into the bundle.
   M365 **Copilot** already does RAG over this content — the "fast answers, not
   trusted answers" problem the [hallucination-baking risk](../concepts/hallucination-baking-risk.md)
   names.
2. **Bundle store (M365-native).** Keep the [OKF bundle](../concepts/open-knowledge-format.md)
   in a document library, because the mappings are clean (below).
3. **Query + presentation layer.** Surface the compiled bundle to **M365 Copilot**
   (via a **Graph connector**) or as SharePoint pages — so Copilot answers from the
   compiled, attested bundle, not raw docs. A fourth
   [presentation-layer](../concepts/presentation-layer.md) option (enterprise/M365).

## Mapping (OKF ↔ SharePoint)
| OKF / LLM-wiki | SharePoint |
|---|---|
| YAML frontmatter (`type`, `status`, `verified`, `stale_after`) | metadata columns / content types |
| [verified trust tier](../concepts/provenance-and-trust.md) / sign-off | approval workflows (Power Automate), check-in/out |
| `log.md` + versioning | native version history |
| per-user privacy | permissions + sensitivity labels |
| [lint](../concepts/three-operations.md) / staleness | scheduled Power Automate flows + retention labels |

## Frictions
- **Not Markdown/git-native** — no out-of-the-box bidirectional sync like
  [GitBook](gitbook.md)'s Git Sync; frontmatter ↔ metadata-column round-trip needs
  Power Automate / Graph / a sync script.
- Markdown doesn't render as pages natively (needs a web part / SPFx, or publishing
  as pages).
- **Compile / lint / attest still run outside SharePoint** — an agent with Graph
  access + CI. SharePoint stores, versions, governs, and serves; it doesn't compile.

## Pragmatic recommendation
Bundle stays in **git** (source of truth, LLM-maintained, CI-attested); integrate
SharePoint on both ends — **ingest** from it via Graph, and **surface** the compiled
bundle to Copilot via a Graph connector, using SharePoint approvals as the
human-reviewed gate.

## Related
- [Presentation layer](../concepts/presentation-layer.md) · [GitBook](gitbook.md) · [Model Context Protocol](../concepts/model-context-protocol.md)
- [One Data, One Meaning](../summaries/one-data-one-meaning.md) — the governance/privacy motivation.
