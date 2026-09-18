---
title: OKF profile
type: concept
tags: [okf, profile, edtech, metadata, extensibility, standards]
status: draft
created: 2026-09-18
updated: 2026-09-18
sources: [source-molenaar-one-data-one-meaning, source-okf-spec]
---

# OKF profile

A **domain-specific tightening of [OKF](open-knowledge-format.md)**: OKF is
deliberately minimal (only `type` is required, producers invent their own types),
so a community that wants consistency across bundles defines a *profile* — an agreed
set of `type` values, metadata fields/tags, and conventions for its domain.

## Why a profile is needed
OKF's openness is a feature and a gap: two edtech bundles could both conform yet
share no vocabulary. [Molenaar & Nörenberg](../sources/source-molenaar-one-data-one-meaning.md)
propose, as a next step, an **OKF Profile for (1)EdTech standards** — specific
metadata fields/tags so a Caliper bundle, a QTI bundle, and a OneRoster bundle line
up and can be reasoned over together. This is the same move HTML microformats or
Dublin Core profiles make on top of a permissive base format.

## What it would pin down
- A closed set of edtech `type`s (e.g. `Spec`, `DataModelObject`, `Metric`,
  `ContextDefinition`) atop OKF's open typing.
- Required metadata (spec + version, conformance-clause references, governance
  owner) beyond OKF's optional fields.
- Conventions for [context dictionaries](context-dictionary.md) and
  [attested conformance](attested-computation.md) checks.

Compare this wiki's own closed page-type set — a small, informal profile of OKF for
a link wiki (see [OKF vs this wiki's schema](../summaries/okf-vs-this-wiki-schema.md)).

## Sources
- [Molenaar & Nörenberg — One Data, One Meaning](../sources/source-molenaar-one-data-one-meaning.md)
- [OKF Specification v0.2](../sources/source-okf-spec.md)

## Related
- [Open Knowledge Format](open-knowledge-format.md) · [Applying OKF to 1EdTech specs](../summaries/okf-for-1edtech-specs.md)
