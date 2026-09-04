---
title: "1EdTech — AI-Ready Query Interfaces (EduQuery proposal)"
type: source
tags: [edtech, 1edtech, eduquery, mcp, graphql, semantics, privacy, standards]
status: stable
created: 2026-09-04
updated: 2026-09-04
url: "file: C:/Users/markm/OneDrive/Documenten/1EdTech/EduQuery/AI-Ready Query Interfaces.pdf"
author: Tim Couper (Chief Architect, 1EdTech)
published: unknown
accessed: 2026-09-04
source_type: slides
link_status: live
---

# 1EdTech — AI-Ready Query Interfaces (EduQuery proposal)

**A 1EdTech conference deck proposing "EduQuery": a standards-based, privacy-centric, MCP + GraphQL interface that lets AI query education data against a shared, spec-aligned data model.** _(Private local presentation, 41 slides.)_

## Summary
Tim Couper frames four use cases — AI learning assistants, institution-wide
insights, privacy-first analytics, and standards for accessing data — then the
blockers: bespoke per-institution data pipelines, instance-level (not per-user)
auth, and no common semantics ("no common definition of what it means"). The
proposal, **EduQuery**, is a common interface any data source (LMS, SIS, learning
tools, pipelines) can expose: `discover()` to find available data, a **Query
Schema**, prompts/instructions for MCP hosts, and a **common abstract data model
aligned with existing 1EdTech standards**; `ask(<query>)` returns data while
enforcing auth and privacy. It uses **GraphQL** (LLMs already translate English →
GraphQL) with 1EdTech-aligned semantics, and rides **MCP** as the transport. Status:
open-source proof of concept, seeking a working group.

## Key claims / quotes
- The core gap: "no common definition of what it means" — data can be fetched but
  not understood. → [The unified-semantics gap](../concepts/unified-semantics-gap.md)
- **MCP** is "USB for AI" — a universal, modular, secure way for AI to discover and
  access tools/data (from Anthropic, Nov 2024); auth is per-session. → [Model Context Protocol](../concepts/model-context-protocol.md)
- EduQuery supplies the **shared schema / abstract data model** aligned to 1EdTech
  standards, so an AI knows what it can ask and what the returned data means. →
  [EduQuery](../entities/eduquery.md)
- Privacy must be **per-user/per-request**, role-aware, exposing only what's
  necessary — not the current instance-level pattern.
- Design stance: adopt best-of-breed (GraphQL, MCP), target only unsolved problems,
  purpose is enabling AI (analytics is a side benefit).

## Why it matters here
This deck is a real, domain-specific instance of the problem OKF and the LLM wiki
exist to solve: fragmented sources with no shared meaning. Its "abstract data model
aligned with 1EdTech standards" is, in effect, the thing an
[OKF bundle of specs](../summaries/okf-for-1edtech-specs.md) would be — a shared,
machine-readable semantic + conformance layer that an AI reads instead of guessing.
It also ties the wiki's [MCP](../concepts/model-context-protocol.md) thread to a
concrete consumer.

## Feeds
- [Applying OKF / the LLM wiki to 1EdTech specs](../summaries/okf-for-1edtech-specs.md)
- [The unified-semantics gap](../concepts/unified-semantics-gap.md)
- [Model Context Protocol](../concepts/model-context-protocol.md)
- [EduQuery](../entities/eduquery.md) · [1EdTech](../entities/1edtech.md) · [Tim Couper](../entities/tim-couper.md)
