---
title: The unified-semantics gap
type: concept
tags: [semantics, standards, data, interoperability, edtech]
status: draft
created: 2026-09-04
updated: 2026-09-18
sources: [source-1edtech-eduquery-ai-ready-query, source-molenaar-one-data-one-meaning]
---

# The unified-semantics gap

A distinct failure mode from simply not having the data: you *can* fetch the data
but there's **no common definition of what it means**. The
[EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md) names this as
the crux for education data — "even when you do get the data, no common definition
of what it means."

## Why it's its own problem
- **Access ≠ understanding.** APIs and MCP can deliver bytes; they don't guarantee
  two systems agree on what a "completion", a "grade", or a "result" *is*.
- Each institution/app exposes data differently, with query languages and data
  models "driven by the data infrastructure" rather than a shared standard.
- For an AI, ambiguous semantics are dangerous: it will confidently interpret a
  field the wrong way. This is the [hallucination-baking risk](hallucination-baking-risk.md)
  at the schema level.

## The sharpest example
[Molenaar & Nörenberg](../sources/source-molenaar-one-data-one-meaning.md) make it
concrete: a Caliper "Completed" event is transmitted intact, yet the data means
"reached the last page," the teacher assumes understanding, and the student assumes
mastery — "the data is interoperable; its contextual interpretation is not." Their
fix, a [context dictionary](context-dictionary.md), is this gap's remedy in one
artifact.

## Relation to the LLM wiki / OKF
This is the [context-assembly problem](context-assembly-problem.md) seen from the
*meaning* side rather than the *location* side. The fix is the same shape: a
shared, machine-readable knowledge layer that pins definitions once. An
[OKF bundle of specs](../summaries/okf-for-1edtech-specs.md) supplies exactly that —
the abstract data model and definitions an AI reads instead of guessing, with
conformance checkable rather than assumed.

## Sources
- [1EdTech — EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md)
- [Molenaar & Nörenberg — One Data, One Meaning](../sources/source-molenaar-one-data-one-meaning.md)

## Related
- [Context dictionary](context-dictionary.md) · [The context-assembly problem](context-assembly-problem.md) · [Open Knowledge Format](open-knowledge-format.md)
- [Applying OKF / the LLM wiki to 1EdTech specs](../summaries/okf-for-1edtech-specs.md) · [One Data, One Meaning](../summaries/one-data-one-meaning.md)
