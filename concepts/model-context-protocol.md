---
title: Model Context Protocol (MCP)
type: concept
tags: [mcp, agents, protocol, anthropic, data-access]
status: draft
created: 2026-09-04
updated: 2026-09-04
sources: [source-1edtech-eduquery-ai-ready-query]
---

# Model Context Protocol (MCP)

An open protocol ("USB for AI") for connecting AI systems to external tools and
data in a uniform, modular, secure way. From [Anthropic](../entities/anthropic.md)
(Nov 2024); the [EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md)
uses it as the transport for standards-based education-data access.

## What it provides
- A universal way for AI/apps to **discover, connect to, and use** tools or data.
- Multiple transports (stdio and HTTP streams); growing adoption.
- Basic authentication — **per MCP session** (a limitation the EduQuery proposal
  flags: it wants per-user/per-request, role-aware access instead).

## Why it's in this wiki
MCP is the pipe; it does not, by itself, supply **meaning**. It solves *access*,
not the [unified-semantics gap](unified-semantics-gap.md). That makes it a natural
consumer of an [OKF](open-knowledge-format.md) knowledge layer: MCP delivers the
data and the schema; an OKF bundle of specs defines what the data *means* and
whether an implementation conforms. MCP also appears elsewhere in the wiki's world —
the [AI-native SDLC](../summaries/llm-wiki-applied-to-sdlc.md) governs MCP
allowlists as part of its managed settings.

## Sources
- [1EdTech — EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md)

## Related
- [EduQuery](../entities/eduquery.md) · [The unified-semantics gap](unified-semantics-gap.md) · [Open Knowledge Format](open-knowledge-format.md)
