# Change log

Append-only, newest at the bottom. One block per action. Never edit past entries;
correct via a new entry. Format defined in [CLAUDE.md](CLAUDE.md) §6.

## 2026-09-02  ·  ingest
- action: seeded the wiki and ingested Karpathy's "LLM Wiki" gist as the first source
- pages: [source-karpathy-llm-wiki-gist, concepts/three-layer-architecture, entities/andrej-karpathy, summaries/llm-wiki-vs-rag, index]
- note: created initial folder structure and a worked example spanning all page types; source captured verbatim-substance to survive link rot.

## 2026-09-02  ·  ingest
- action: ingested Joshi's Medium walkthrough (first secondary source); fetched via in-app browser after Medium 403'd the plain fetch
- pages: [source-joshi-medium-llm-wiki, concepts/knowledge-compilation-analogy, concepts/three-operations, concepts/hallucination-baking-risk, concepts/memex, entities/urvil-joshi, entities/vannevar-bush, entities/obsidian]
- note: created 4 concept + 3 entity pages.
- action: densified existing pages with the new source's framings
- pages: [concepts/three-layer-architecture, summaries/llm-wiki-vs-rag, entities/andrej-karpathy, index]
- note: added compilation analogy + AGENTS.md alt to architecture; expanded the RAG comparison table (traceability, freshness, error blast radius, corpus size) and added the "neither wins" section; added tweet origin + quotes to Karpathy. No contradictions with the gist — the article extends it.

## 2026-09-02  ·  ingest
- action: ingested two OKF sources together — Google Cloud's OKF blog and the OKF v0.2 SPEC.md (both via WebFetch; GitHub raw for the spec)
- pages: [source-google-okf-blog, source-okf-spec, concepts/open-knowledge-format, concepts/knowledge-bundle, concepts/provenance-and-trust, concepts/attested-computation, concepts/context-assembly-problem, entities/sam-mcveety, entities/amir-hormati, entities/google-cloud-knowledge-catalog, summaries/okf-vs-this-wiki-schema]
- note: OKF explicitly formalizes the LLM-wiki pattern; created 5 concept + 3 entity pages and a synthesis comparing OKF to this wiki's own CLAUDE.md schema.
- action: densified existing pages with OKF connections
- pages: [concepts/hallucination-baking-risk, concepts/three-layer-architecture, concepts/three-operations, entities/andrej-karpathy, index]
- note: keyed OKF's trust tiers / stale_after / attestation to the hallucination-risk page as concrete mitigations; noted OKF standardizes the wiki layer; linked OKF's index/log/trust into the three-operations page; recorded OKF as downstream influence on Karpathy. No contradictions — OKF is a superset formalization of the pattern.

## 2026-09-02  ·  maintenance
- action: upgraded the schema to CLAUDE.md v2.0 (OKF v0.2 conformance)
- pages: [CLAUDE.md, index, summaries/okf-vs-this-wiki-schema]
- note: added §9 (field mapping, trust family, minimal-conformance rule, non-adopted parts); switched lifecycle values to OKF draft/stable/deprecated; added optional stale_after + generated/verified trust family with actor convention; declared okf_version "0.2" in index.md frontmatter; demonstrated `generated` on the schema-comparison summary. User-authorized schema change.
- action: migrated existing pages to the v2 lifecycle vocabulary
- pages: [concepts/memex, entities/andrej-karpathy, entities/urvil-joshi, entities/vannevar-bush, entities/obsidian, entities/sam-mcveety, entities/amir-hormati, entities/google-cloud-knowledge-catalog]
- note: status: stub → status: draft on all 8 stub pages (body "_Stub._" notes kept). Bundle now conforms: every non-reserved .md has a non-empty type.

## 2026-09-02  ·  synthesize
- action: added Mermaid diagrams to the two core concept pages
- pages: [concepts/three-layer-architecture, concepts/three-operations]
- note: embedded ```mermaid flowcharts (an "At a glance" section on each) — stays plain-text/cat-able per OKF ethos; confirmed rendering in Obsidian and via a standalone Mermaid v10 render check.

## 2026-09-02  ·  synthesize
- action: exported slide-ready images of the two diagrams to assets/
- pages: [assets/three-layer-architecture.png, assets/three-layer-architecture.svg, assets/three-operations.png, assets/three-operations.svg]
- note: rendered the wiki's Mermaid at 3x on a white background; PNGs (~2400–2600px wide) for drop-in slide use, SVGs for scalable/editable use. Source of truth stays the .md diagrams; regenerate from those if edited.

## 2026-09-04  ·  ingest
- action: ingested Anthropic's AI-Native SDLC Playbook (first source that *applies* the pattern, not just describes it)
- pages: [source-anthropic-ai-native-sdlc, summaries/llm-wiki-applied-to-sdlc, concepts/flow-through-vs-compounding-artifacts, entities/anthropic]
- note: created 1 summary + 1 concept + 1 entity; the summary maps the wiki's three layers/operations onto the playbook's six stages and ties OKF trust/attestation to its governance (separation of duties, evals, control bands).
- action: densified existing pages with the SDLC angle
- pages: [concepts/hallucination-baking-risk, concepts/knowledge-compilation-analogy, index]
- note: added a "higher stakes in a codebase" section keying evals/attestation to the risk page; linked the new flow-through-vs-compounding concept from the compilation analogy. No contradictions — the playbook is an application of the pattern. Local only (not committed/pushed).
