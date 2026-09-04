---
title: "Anthropic — The AI-Native SDLC Playbook"
type: source
tags: [sdlc, agents, claude-code, workflow, governance, markdown]
status: stable
created: 2026-09-04
updated: 2026-09-04
url: https://claude.com/blog/the-ai-native-sdlc-playbook
author: Anthropic
published: unknown
accessed: 2026-09-04
source_type: blog
link_status: live
---

# Anthropic — The AI-Native SDLC Playbook   ·   [blog](https://claude.com/blog/the-ai-native-sdlc-playbook)

**A six-stage model for embedding AI agents across the software lifecycle while humans keep judgment — built, like the LLM wiki, on versioned Markdown artifacts.**

## Summary
The playbook reimagines the software development lifecycle around agents at every
stage, with humans accountable for judgment. Its thesis: "Code is no longer the
bottleneck — the human-speed steps around it are." Work flows through six stages —
**Plan → Design → Build → Test → Deploy → Maintain** — each producing a versioned
Markdown artifact (`intent.md`, `spec.md`, `plan.md`), governed by `CLAUDE.md`
(institutional conventions, kept under a page) and `REVIEW.md` (review policy).
Skills advise, hooks enforce, subagents scope recurring tasks, and evals
regression-test agent configuration. The loop closes when monitoring agents detect
anomalies, invoke Claude non-interactively, and file findings as new `intent.md`
that re-enter the pipeline. Governance is layered: "The loop keeps running. Human
judgement stays above it."

## Key claims / quotes
- Six stages, each with a Markdown artifact: Plan (`intent.md`), Design (`spec.md`),
  Build (`plan.md` + `CLAUDE.md`), Test (evals), Deploy (PR review + hooks),
  Maintain (monitoring → new `intent.md`).
- Institutional knowledge is carried by **`CLAUDE.md`** (capped at ~one page),
  Skills (advisory), Hooks (deterministic gates), Subagents, and Evals.
- **Separation of duties**: agents cannot approve their own work; humans own every
  judgment call. → [Provenance and trust](../concepts/provenance-and-trust.md)
- The Maintain stage is a closed loop: findings become `intent.md` and restart the
  pipeline — an ingestion-shaped event.

## Why it matters here
This is the wiki's first source that is a *real-world application* of the LLM-wiki
pattern rather than a description of it. It runs on the same substrate the wiki does
(versioned Markdown + `CLAUDE.md`), which makes it the sharpest case study for what
the pattern adds to a team workflow: a persistent, compounding knowledge layer
beside a pipeline that currently produces mostly flow-through artifacts.

## Feeds
- [Applying the LLM wiki to the AI-native SDLC](../summaries/llm-wiki-applied-to-sdlc.md)
- [Flow-through vs compounding artifacts](../concepts/flow-through-vs-compounding-artifacts.md)
- [Anthropic](../entities/anthropic.md)
- [Hallucination-baking risk](../concepts/hallucination-baking-risk.md) · [Provenance and trust](../concepts/provenance-and-trust.md)
