---
title: "Google Cloud — How the Open Knowledge Format can improve data sharing"
type: source
tags: [okf, llm-wiki, google-cloud, data-sharing, agents, standard]
status: stable
created: 2026-09-02
updated: 2026-09-02
url: https://cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing
author: Sam McVeety & Amir Hormati (Google Cloud)
published: 2026-06-12
accessed: 2026-09-02
source_type: blog
link_status: live
---

# Google Cloud — How the Open Knowledge Format can improve data sharing   ·   [blog](https://cloud.google.com/blog/products/data-analytics/how-the-open-knowledge-format-can-improve-data-sharing)

**Google Cloud's announcement of the Open Knowledge Format (OKF): an open, vendor-neutral spec that formalizes the LLM-wiki pattern into a portable, interoperable format for AI systems.**

## Summary
McVeety and Hormati argue that organizational knowledge is scattered across
incompatible systems — metadata catalogs, wikis, code comments, senior engineers'
heads — so every agent builder re-solves the same context-assembly problem and
every catalog vendor reinvents the same data models. OKF is their proposed fix: a
directory of markdown files with YAML frontmatter, simple conventions, and no
required SDK, runtime, or proprietary account. It explicitly generalizes Karpathy's
LLM-wiki idea into a shared, portable **format** (not a platform) that agents can
read and update as it grows more useful over time. Google Cloud's Knowledge
Catalog was updated to ingest OKF bundles and serve them to agents.

## Key claims / quotes
- OKF "formalizes the LLM-wiki pattern" into a portable, interoperable spec. →
  [Open Knowledge Format](../concepts/open-knowledge-format.md)
- Problem framing (article): "Every agent builder is solving the same
  context-assembly problem from scratch." → [The context-assembly problem](../concepts/context-assembly-problem.md)
- Cites Karpathy: LLMs "don't get bored, don't forget to update a cross-reference,
  and can touch 15 files in one pass." → [Andrej Karpathy](../entities/andrej-karpathy.md)
- Design principles: minimally opinionated (only `type` required),
  producer/consumer independence, "format, not platform" (vendor-neutral).
- "The format itself is the contribution" — positioned as a lingua franca for
  knowledge exchange.
- Google Cloud ships reference implementations: an enrichment agent that walks
  BigQuery datasets and drafts OKF docs, and a static-HTML graph visualizer. →
  [Google Cloud Knowledge Catalog](../entities/google-cloud-knowledge-catalog.md)

## Why it matters here
This source moves the wiki's topic from an *idea/pattern* (Karpathy) and a
*tutorial* (Joshi) to an *open standard*. It is direct evidence that the LLM-wiki
pattern is being formalized industry-side, and it introduces the mechanisms —
provenance, trust, attestation — that address the pattern's known weaknesses.

## Feeds
- [Open Knowledge Format](../concepts/open-knowledge-format.md)
- [The context-assembly problem](../concepts/context-assembly-problem.md)
- [Google Cloud Knowledge Catalog](../entities/google-cloud-knowledge-catalog.md)
- [Sam McVeety](../entities/sam-mcveety.md) · [Amir Hormati](../entities/amir-hormati.md) · [Andrej Karpathy](../entities/andrej-karpathy.md)
