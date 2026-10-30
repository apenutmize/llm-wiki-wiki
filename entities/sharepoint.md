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

## Implementation sketch
A plausible build (one-way publish, the lowest-conflict option):

1. **Source of truth stays in git.** The [LLM maintainer](../concepts/three-layer-architecture.md)
   compiles/lints the bundle; CI (e.g. GitHub Actions) runs on merge.
2. **Library + content types.** In the target site, create a document library with a
   **content type per OKF `type`** (Concept, Entity, Summary, Source) and **site
   columns** mirroring the frontmatter: `status` (Choice), `verified` (Person + date),
   `stale_after` (Date), `sources` (text/lookup), `type` (Choice). The `.md` body is
   the file; the frontmatter is also projected into columns for search, filtering, and
   governance.
3. **Publish step (Microsoft Graph).** On merge, CI authenticates as an **Entra ID app
   registration** (least-privilege **`Sites.Selected`** scoped to the one site; secret
   in Key Vault) and, per page, **upserts the file** and **sets the list-item fields**
   from the parsed frontmatter via the Graph `driveItem` / `listItem fields` endpoints.
4. **Trust gate.** Use the library's **content-approval** setting (or a Power Automate
   approval) so a human sign-off flips `verified` → the
   [human-reviewed tier](../concepts/provenance-and-trust.md); apply **sensitivity
   labels** for privacy.
5. **Serve humans.** Readers browse the library and **Microsoft Search**; for a nicer
   surface, generate **SharePoint pages** from the content or use a markdown-rendering
   / SPFx web part (native `.md` rendering is weak — see Frictions).
6. **Serve agents.** Expose the library to **M365 Copilot** (it indexes SharePoint, or
   register a **Graph connector**) so Copilot answers from the compiled, attested
   bundle; agents outside M365 can read it via the Graph API or an MCP server wrapping
   Graph.
7. **Lint / staleness.** A scheduled **Power Automate** flow (or the agent's lint pass
   over Graph) flags items past `stale_after` and surfaces orphans/broken links.

Going **two-way** (editing in SharePoint *and* git) is possible but adds a reverse
sync that reads changed list items back to git — keep **git as the conflict tiebreaker**,
mirroring the "pull before push" discipline.

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
