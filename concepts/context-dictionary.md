---
title: Context dictionary
type: concept
tags: [semantics, learning-analytics, caliper, meaning, okf]
status: draft
created: 2026-09-18
updated: 2026-09-18
sources: [source-molenaar-one-data-one-meaning]
---

# Context dictionary

The concrete artifact that closes the [unified-semantics gap](unified-semantics-gap.md):
a shared, authoritative mapping from a data field to *what it actually means* — so
the same event becomes an actionable decision rather than a guess.

## The worked example (learning analytics)
[Molenaar & Nörenberg](../sources/source-molenaar-one-data-one-meaning.md) show a
"Completed" event that is transmitted intact between systems yet interpreted three
different ways — the data logs "reached the last page," the teacher assumes
understanding, the student assumes mastery. A context dictionary states the shared
meaning explicitly:
- **"Completed"** = last page reached, *not* understanding shown.
- **"Score 80%"** = 8 of 10 items correct, difficulty unknown.
- **"12 minutes"** = time on page, *not* time on task.

"Shared meaning turns the same data into a teaching decision."

## Why it's an OKF/LLM-wiki artifact
A context dictionary is exactly what a [concept page](three-layer-architecture.md)
in an [OKF bundle](open-knowledge-format.md) holds: a term defined once,
authoritative ([human-reviewed](provenance-and-trust.md)), cross-linked to the spec
it comes from. The talk's proposed "Caliper Analytics Context Dictionary OKF" is a
context dictionary published as a bundle — the meaning half of
[EduQuery](../entities/eduquery.md), served to humans and agents alike.

## Sources
- [Molenaar & Nörenberg — One Data, One Meaning](../sources/source-molenaar-one-data-one-meaning.md)

## Related
- [The unified-semantics gap](unified-semantics-gap.md) · [Caliper Analytics](../entities/caliper-analytics.md)
- [One Data, One Meaning](../summaries/one-data-one-meaning.md) · [OKF profile](okf-profile.md)
