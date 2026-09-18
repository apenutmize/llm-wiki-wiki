---
title: "Molenaar & Nörenberg — One Data, One Meaning (Learning Impact Europe 2026)"
type: source
tags: [edtech, learning-analytics, caliper, okf, llm-wiki, eduquery, semantics, cornelsen, own-work]
status: stable
created: 2026-09-18
updated: 2026-09-18
url: "file: C:/Users/markm/OneDrive/Documenten/Conferences/Learning Impact Europe 2026 Thessaloniki/Knowledge Management FINAL print.pdf"
author: Mark Molenaar (ApeNutMize) & Lennart Nörenberg (Cornelsen Verlag)
published: 2026
accessed: 2026-09-18
source_type: slides
link_status: live
---

# Molenaar & Nörenberg — One Data, One Meaning: AI Enabling Interpretation for Learning Analytics

**The user's own Learning Impact Europe 2026 (Thessaloniki) talk — the capstone that ties this wiki's threads together: EdTech data is interoperable, but its *interpretation* is not, and an OKF/LLM-Wiki bundle supplies the shared meaning.** _(Private local presentation, 21 slides; cites this very repo.)_

## Summary
The thesis: EdTech standards give strong *technical* interoperability — data,
events, and learner activity flow reliably between platforms — but "the data is
interoperable; its contextual interpretation is not." The worked example: a
"Completed" event logs only "reached the last page," yet the teacher assumes
understanding and the student assumes mastery. The fix is a **shared meaning /
context dictionary** ("Completed" = last page reached, not understanding shown;
"Score 80%" = 8 of 10 items correct, difficulty unknown; "12 minutes" = time on
page, not time on task) so the same event becomes an actionable teaching decision.
The talk then walks the wiki's own stack — 1EdTech standards → MCP & EduQuery →
LLM Wiki (Karpathy) & OKF (Google Cloud) — and presents a proof of concept:
**Caliper Analytics as an OKF/LLM-Wiki bundle**, editable in Obsidian + Claude
Code, where "one architecture can serve humans and Agents alike."

## Key claims / quotes
- Thesis: "The data is interoperable. Its contextual interpretation is not." →
  [The unified-semantics gap](../concepts/unified-semantics-gap.md)
- "Shared meaning turns the same data into a teaching decision." — via a context
  dictionary. → [Context dictionary](../concepts/context-dictionary.md)
- PoC: **Caliper Analytics specification as an OKF/LLM-Wiki bundle**; two components
  enable any LLM-Wiki — a Markdown editor (Obsidian) + an agent harness/LLM
  (Claude Code). → [Caliper Analytics](../entities/caliper-analytics.md)
- "One Architecture can serve humans and Agents alike."
- Next steps: define an **OKF Profile for (1)EdTech standards** (specific metadata
  fields/tags), apply the pattern to Caliper (a "Context Dictionary OKF"),
  OneRoster/EduAPI, QTI, LTI, CASE, the Student Learning Data Model, and into
  AI-native SDLCs; revisit EduQuery with LLM-Wiki/OKF context. → [OKF profile](../concepts/okf-profile.md)
- Cites the LLM Wiki (Karpathy) & OKF (Google Cloud) — and this repo,
  `github.com/apenutmize/llm-wiki-wiki`, as its source.

## Why it matters here
This is the user's own synthesis and the wiki's capstone: every prior source
(1EdTech, MCP, EduQuery/Couper, Karpathy, OKF, AI-native SDLC, Caliper) converges
here into a concrete framing ("One Data, One Meaning") and a running PoC. It is
also **self-referential** — the wiki this note lives in is a cited artifact of the
talk — which is exactly the compounding loop the pattern predicts. It contributes
the [context dictionary](../concepts/context-dictionary.md) and
[OKF profile](../concepts/okf-profile.md) ideas.

## Feeds
- [One Data, One Meaning](../summaries/one-data-one-meaning.md)
- [Context dictionary](../concepts/context-dictionary.md) · [OKF profile](../concepts/okf-profile.md)
- [Caliper Analytics](../entities/caliper-analytics.md)
- [Mark Molenaar](../entities/mark-molenaar.md) · [Lennart Nörenberg](../entities/lennart-norenberg.md) · [Cornelsen](../entities/cornelsen.md)
