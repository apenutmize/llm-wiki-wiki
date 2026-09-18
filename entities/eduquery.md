---
title: EduQuery
type: entity
tags: [project, proposal, edtech, mcp, graphql, standards, privacy]
status: draft
created: 2026-09-04
updated: 2026-09-18
sources: [source-1edtech-eduquery-ai-ready-query, source-molenaar-one-data-one-meaning]
---

# EduQuery

A [1EdTech](1edtech.md) proposal (open-source proof of concept) for a common,
standards-based, privacy-centric interface that lets AI query education data across
systems. Any data source (LMS, SIS, learning tools, pipelines) can expose it.

## Shape
- `discover()` — find what data is available.
- **Query Schema** + prompts/instructions for MCP hosts.
- A **common abstract data model aligned with existing 1EdTech standards** —
  extensible; defines what returned data means.
- `ask(<query>)` — returns data while enforcing auth and privacy.
- Built on **[GraphQL](../concepts/model-context-protocol.md)** (LLMs translate
  English → GraphQL against a shared schema) and delivered over **MCP**.
- Privacy stance: per-user/per-request, role-aware, expose only what's necessary.

## Relevance to this wiki
EduQuery's "abstract data model aligned with 1EdTech standards" is functionally an
[OKF bundle of specs](../summaries/okf-for-1edtech-specs.md): the shared semantic
layer an AI reads. EduQuery is the *access + query* surface; an OKF bundle is the
*meaning + conformance* surface behind it. Together they close both halves of the
[unified-semantics gap](../concepts/unified-semantics-gap.md).

## The experiment, in one line
Per [Molenaar & Nörenberg](../sources/source-molenaar-one-data-one-meaning.md),
EduQuery (an early 1EdTech experiment, June 2025) takes data **in** via EduAPI and
Caliper, queries it through **GraphQL**, and exposes it **out** over MCP (for
AI/LLMs), LTI (for tools), and REST (for analytics) — reusing 1EdTech's existing
security/privacy frameworks. It is still a concept, not a released standard, and
could add xAPI, CASE, and QTI Results Reporting. The talk's proposal: attach
LLM-Wiki/OKF **context** to it, closing the meaning gap it leaves open.

## Sources
- [1EdTech — EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md)
- [Molenaar & Nörenberg — One Data, One Meaning](../sources/source-molenaar-one-data-one-meaning.md)

## Related
- [Model Context Protocol](../concepts/model-context-protocol.md) · [Applying OKF to 1EdTech specs](../summaries/okf-for-1edtech-specs.md)
- [One Data, One Meaning](../summaries/one-data-one-meaning.md) · [Caliper Analytics](caliper-analytics.md)
