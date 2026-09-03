---
title: Obsidian
type: entity
tags: [tool, viewer, markdown, obsidian]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-joshi-medium-llm-wiki]
---

# Obsidian

A free local Markdown knowledge-base application (obsidian.md). In the LLM-wiki
pattern it plays the role of the **viewer** over the vault the LLM maintains.

## Relevance to this wiki
- Joshi's walkthrough uses Obsidian to open the vault and render the **graph view**
  — nodes are pages, edges are the `[[wikilinks]]` the model added — making the
  compounding density of the wiki visible.
- Captures the role split Karpathy states (as quoted by Joshi): "Obsidian is the
  IDE; the LLM is the programmer; the wiki is the codebase." See
  [Knowledge as compilation](../concepts/knowledge-compilation-analogy.md).

## Note for this wiki
This wiki currently uses **relative Markdown links** rather than Obsidian-style
`[[wikilinks]]` (see [CLAUDE.md](../CLAUDE.md) §4.3). Obsidian can still open the
folder; only the link syntax differs.

## Sources
- [Joshi — LLM Wiki walkthrough](../sources/source-joshi-medium-llm-wiki.md)
