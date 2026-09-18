---
title: One Data, One Meaning
type: summary
tags: [learning-analytics, semantics, caliper, okf, llm-wiki, eduquery, capstone]
status: draft
created: 2026-09-18
updated: 2026-09-18
sources: [source-molenaar-one-data-one-meaning, source-1edtech-eduquery-ai-ready-query, source-aracil-standards-adoption, source-karpathy-llm-wiki-gist, source-google-okf-blog]
generated: { by: claude-code/opus-4.8, at: 2026-09-18T00:00:00Z }
---

# One Data, One Meaning

The [Molenaar & Nörenberg talk](../sources/source-molenaar-one-data-one-meaning.md)
(Learning Impact Europe 2026) is this wiki's capstone: it takes every thread the
wiki has ingested and lands them on one problem in learning analytics — **the data
is interoperable, but its interpretation is not** — and one answer: publish the
shared meaning as an OKF/LLM-Wiki bundle.

## At a glance

```mermaid
flowchart TB
    EV["📎 'Completed' event (Caliper)<br/>transmitted intact between systems"]

    subgraph AMB["Without shared meaning — divergent readings"]
        direction LR
        D1["Data logs:<br/>reached the last page"]
        T1["Teacher assumes:<br/>they understood it"]
        S1["Student thinks:<br/>I've mastered it"]
    end
    Q["❓ ambiguity → wrong call<br/>move on too soon"]

    CD(["📖 Context dictionary<br/>'Completed' = last page reached,<br/><i>not</i> understanding shown"])
    DEC["✅ Teaching decision<br/>last page ≠ mastery →<br/>ask one quick question"]

    EV -. "without" .-> AMB --> Q
    EV == "with a context dictionary" ==> CD ==> DEC

    classDef event fill:#e8f0fe,stroke:#4285f4,color:#111;
    classDef bad fill:#fde8e8,stroke:#d9534f,color:#111;
    classDef dict fill:#fef7e0,stroke:#fbbc04,color:#111;
    classDef good fill:#e6f4ea,stroke:#34a853,color:#111;
    class EV event; class D1,T1,S1,Q bad; class CD dict; class DEC good;
```

**Same event, two fates.** Without shared meaning the "Completed" event scatters into
three private readings and a wrong call; run through a
[context dictionary](../concepts/context-dictionary.md) it resolves to one meaning the
teacher can act on. The data was always interoperable — the *dictionary* is what makes
the interpretation interoperable too.

## The gap it names
EdTech standards deliver strong *technical* interoperability: events flow intact
between platforms. But the same Caliper "Completed" event is read three ways — the
data logs "reached the last page," the teacher assumes understanding, the student
assumes mastery. Interoperable transport, incompatible interpretation. This is the
[unified-semantics gap](../concepts/unified-semantics-gap.md) made vivid.

## The answer: a context dictionary
"Shared meaning turns the same data into a teaching decision." A
[context dictionary](../concepts/context-dictionary.md) states each term's meaning
once and authoritatively ("Completed" = last page reached, not understanding shown),
so the event becomes actionable. Published as an [OKF bundle](../concepts/open-knowledge-format.md),
that dictionary is readable by humans *and* agents — "one architecture can serve
humans and Agents alike."

## How it assembles the wiki's parts
The talk walks the exact stack this wiki has built up:
- **1EdTech standards** (OneRoster/EduAPI, Caliper/xAPI, LTI, QTI, CASE) — the
  interoperable-transport layer. See [1EdTech](../entities/1edtech.md).
- **[MCP](../concepts/model-context-protocol.md) & [EduQuery](../entities/eduquery.md)** —
  access and query (Couper's experiment: EduAPI/Caliper in, GraphQL, out over
  MCP/LTI/REST).
- **[LLM Wiki](../sources/source-karpathy-llm-wiki-gist.md) & [OKF](../concepts/open-knowledge-format.md)** —
  the compounding, machine-readable knowledge layer that supplies meaning.
- **PoC:** [Caliper Analytics](../entities/caliper-analytics.md) as an OKF/LLM-Wiki
  bundle, built with just two components — a Markdown editor (Obsidian) + an agent
  harness (Claude Code).

## Next steps it sets
- Define an **[OKF profile for EdTech](../concepts/okf-profile.md)** (agreed
  metadata fields/tags).
- Apply the pattern to Caliper (a "Context Dictionary OKF"), OneRoster/EduAPI, QTI,
  LTI, CASE, the Student Learning Data Model — and feed those specs into
  [AI-native SDLCs](llm-wiki-applied-to-sdlc.md).
- Revisit EduQuery with LLM-Wiki/OKF context attached.

## The self-referential loop
The talk cites this repository as a source. So the wiki is both the **method** it
describes and an **artifact** of the work it reports — the compounding knowledge
base feeding the very presentation that argues for compounding knowledge bases.
That loop is the pattern working as intended, seen from the outside.

## Sources
- [Molenaar & Nörenberg — One Data, One Meaning](../sources/source-molenaar-one-data-one-meaning.md)
- [1EdTech — EduQuery deck](../sources/source-1edtech-eduquery-ai-ready-query.md)
- [1EdTech (Aracil) — standards adoption](../sources/source-aracil-standards-adoption.md)
- [Karpathy — LLM Wiki gist](../sources/source-karpathy-llm-wiki-gist.md)
- [Google Cloud — OKF blog](../sources/source-google-okf-blog.md)

## Related
- [Applying OKF to 1EdTech specs](okf-for-1edtech-specs.md) · [Context dictionary](../concepts/context-dictionary.md) · [OKF profile](../concepts/okf-profile.md)
