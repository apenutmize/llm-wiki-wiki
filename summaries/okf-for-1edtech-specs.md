---
title: Applying OKF / the LLM wiki to 1EdTech specs
type: summary
tags: [okf, 1edtech, eduquery, semantics, conformance, mcp, application]
status: draft
created: 2026-09-04
updated: 2026-09-16
sources: [source-1edtech-eduquery-ai-ready-query, source-aracil-standards-adoption, source-okf-spec, source-google-okf-blog, source-anthropic-ai-native-sdlc]
generated: { by: claude-code/opus-4.8, at: 2026-09-04T00:00:00Z }
---

# Applying OKF / the LLM wiki to 1EdTech specs

The [EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md) needs one
thing it can't get from a query protocol alone: a **shared, authoritative,
machine-readable definition of what education data means**, plus a way to check that
an implementation actually follows it. That is precisely what an
[Open Knowledge Format](../concepts/open-knowledge-format.md) bundle provides. So the
LLM-wiki pattern maps onto 1EdTech in a very direct way: **an OKF bundle of 1EdTech
specs as the semantic + conformance layer behind EduQuery.**

## At a glance

```mermaid
flowchart TB
    AI["🤖 AI assistant / app<br/>asks in natural language"]
    SK["🛠️ Skills — procedures (verbs)<br/>build · validate · migrate<br/><i>thin; point into the bundle</i>"]
    EQ["EduQuery<br/>GraphQL · discover() / ask()<br/>over MCP · per-user auth & privacy"]
    DS["Data sources<br/>LMS · SIS · learning tools · pipelines"]
    KB(["📚 OKF bundle of 1EdTech specs — knowledge (nouns)<br/>definitions · abstract data model<br/>cross-spec mappings · <b>attested</b> conformance"])
    SPEC["1EdTech specs<br/>Caliper · OneRoster · QTI · CASE<br/><i>immutable raw sources</i>"]

    AI == "English ↔ GraphQL" ==> EQ
    AI -. "triggers" .-> SK
    SK -. "read for authority" .-> KB
    EQ == "ask() over MCP" ==> DS
    EQ -. "reads shared schema<br/>& semantics" .-> KB
    KB -. "attests conformance of" .-> DS
    SPEC --> KB

    classDef ai fill:#e8f0fe,stroke:#4285f4,color:#111;
    classDef access fill:#e6f4ea,stroke:#34a853,color:#111;
    classDef skill fill:#fde8f3,stroke:#c2508f,color:#111;
    classDef bundle fill:#fef7e0,stroke:#fbbc04,color:#111;
    classDef data fill:#f1f3f4,stroke:#9aa0a6,color:#111;
    class AI ai; class EQ access; class SK skill; class KB bundle; class DS,SPEC data;
```

**EduQuery is the access surface; the OKF bundle is the meaning behind it.** The AI
queries in English; EduQuery translates to GraphQL and fetches over MCP; the bundle
supplies the shared schema and definitions EduQuery aligns to, and *attests* that a
data source's endpoint conforms to the standard. The 1EdTech specs stay immutable
raw sources feeding the bundle.

## Two problems, one bundle
The deck names two blockers OKF is well shaped for:
1. **Unified semantics** — "no common definition of what it means." See
   [the unified-semantics gap](../concepts/unified-semantics-gap.md).
2. **Proper implementation** — institutions "expose data differently"; nothing
   proves a given endpoint conforms to the standard.

## The mapping
| OKF bundle of specs | 1EdTech / EduQuery |
|---|---|
| Raw sources (immutable) | The normative spec documents (Caliper, OneRoster, LTI, QTI, CASE, …) |
| entities/ | One page per spec, and per data-model object (Result, LineItem, Assessment, Enrollment) |
| concepts/ | Shared term definitions ("completion", "grade"), cross-spec mappings, conformance rules |
| summaries/ | The **abstract data model** EduQuery aligns to — the cross-spec overview |
| index.md / log.md | Catalog of the standards + a versioned history of definition changes |

## Unified semantics
Each term is defined **once**, in one place, and cross-linked. An AI (via EduQuery's
GraphQL schema and its "prompts/instructions for MCP hosts") reads the definition
instead of inferring it from a field name — closing the meaning half of the gap. The
deck's "common abstract data model aligned with existing 1EdTech standards" *is* this
bundle's summary layer; EduQuery supplies **access + query**, the bundle supplies
**meaning + conformance**.

## Conformance assurance (the strong part)
This is where OKF's governance features earn their place — exactly your "assure
proper implementation of standards":
- **[Attested Computation](../concepts/attested-computation.md)** — encode a spec's
  conformance rule as a *sanctioned, runnable check*. An institution's EduQuery
  endpoint output can be run through the attested validator to **prove** it conforms,
  rather than asserting it does. "Does this implementation follow the standard?"
  becomes a re-runnable gate, not a prose claim.
- **[Verified trust tier](../concepts/provenance-and-trust.md)** — a definition or
  mapping reviewed by 1EdTech is `human-reviewed` (authoritative); a machine-drafted
  one is provisional. Consumers can gate on tier.
- **`stale_after`** — when 1EdTech ships a new spec version, the lint pass flags every
  dependent definition and mapping as stale, so the semantic layer tracks the standard
  instead of drifting from it.

## How EduQuery and MCP consume it
[MCP](../concepts/model-context-protocol.md) is the pipe (access); EduQuery is the
query surface (GraphQL + `discover()`/`ask()`); the OKF bundle is the meaning and
conformance behind both. EduQuery's Query Schema and host instructions can be
generated from — or point directly into — the bundle, so the "shared schema" the deck
promises is literally the bundle served to agents.

## Skills: the procedural layer on top of the bundle
The OKF bundle is **declarative** — the *nouns* of the domain: what a term means,
how specs map, which conformance checks apply. It doesn't, by itself, tell an agent
*when* or *how* to act. That's what **Skills** add — triggerable, procedural
instructions (the *verbs*): "when building an Edu-API provider, do X; authenticate
via OAuth 2.0 client-credentials; omit null values; validate against these checks."

1EdTech already ships this: the [1EdTech AI Enablers](../entities/1edtech-ai-enablers.md)
Model Processing Service packages **Skills** per spec — e.g. an "Edu-API 1.0 Skill"
with activation triggers ("which field represents the role?") and instructions. It's
the same primitive the [AI-native SDLC playbook](../sources/source-anthropic-ai-native-sdlc.md)
calls Skills — "policy encoded as triggerable instructions."

The two layers divide cleanly, and should:
- **Skill (procedure)** — thin, task-triggered; says *how to accomplish* something and
  *points into* the bundle for authority. It should not restate spec text.
- **OKF bundle (knowledge)** — the single authoritative source the Skill reads for
  meaning and the [attested checks](../concepts/attested-computation.md) it runs for
  validation.

Keeping Skills thin and pointing them at the bundle is what stops procedures from
drifting into their own private, unversioned copy of the spec — the
[hallucination-baking risk](../concepts/hallucination-baking-risk.md) applied to
instructions rather than facts. One authoritative bundle can back many Skills
(build, validate, migrate), and each stays current because the meaning lives in the
bundle, not in the Skill.

## The compounding payoff
As institutions implement and their conformance results and local mappings are
ingested back, the bundle accumulates a live picture of *who implements what, and how
well* — which is the deck's second use case (institution-wide insights) emerging from
the knowledge layer rather than from bespoke pipelines.

## 1EdTech is already moving this way
This isn't only a proposal from outside: [Aracil's standards-adoption talk](../sources/source-aracil-standards-adoption.md)
shows 1EdTech independently converging on the same pattern. His
[AI-ready standards](../concepts/ai-ready-standards.md) criteria (structured,
machine-readable, traceable) are the OKF-bundle properties; the
[1EdTech AI Enablers](../entities/1edtech-ai-enablers.md) are its concrete form —
**MR-Specs** ≈ the OKF bundle, **microsites** ≈ its navigation/index layer, **MPS
Skills** ≈ agent-facing instructions, and **conformance workflows** ≈
[attested computation](../concepts/attested-computation.md). His "trusted answers, not
just fast answers — Gen AI over unstructured documents is not enough" is this wiki's
[central thesis](llm-wiki-vs-rag.md) in one line, and "[Working for Both Claudes](../concepts/provenance-and-trust.md)"
is the [verified trust tier](../concepts/provenance-and-trust.md): the machine
retrieves, the human stays authoritative. Where EduQuery is the *runtime query* side,
Aracil covers the *authoring/adoption* side — two halves of the same bundle.

## The one caveat
The bundle must never become an **unaudited second source of truth** that drifts from
the normative specs. Keep the spec documents as immutable
[raw sources](../concepts/three-layer-architecture.md); the bundle *synthesizes and
maps*, and **attests against** the spec rather than restating it — the
[hallucination-baking risk](../concepts/hallucination-baking-risk.md) is acute when
the "facts" are standards other systems must obey.

## Sources
- [1EdTech — EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md)
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)
- [OKF Specification v0.2](../sources/source-okf-spec.md)
- [Google Cloud — OKF blog](../sources/source-google-okf-blog.md)
- [Anthropic — AI-Native SDLC Playbook](../sources/source-anthropic-ai-native-sdlc.md)

## Related
- [The unified-semantics gap](../concepts/unified-semantics-gap.md) · [EduQuery](../entities/eduquery.md) · [Model Context Protocol](../concepts/model-context-protocol.md)
- [Applying the LLM wiki to the AI-native SDLC](llm-wiki-applied-to-sdlc.md) — the same move for a different domain.
