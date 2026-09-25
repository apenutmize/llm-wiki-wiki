---
title: "GitBook — product documentation"
type: source
tags: [gitbook, docs, git-sync, presentation, mcp, llms-txt, tool]
status: stable
created: 2026-09-25
updated: 2026-09-25
url: https://gitbook.com/docs
author: GitBook
published: unknown
accessed: 2026-09-25
source_type: docs
link_status: live
---

# GitBook — product documentation   ·   [gitbook.com/docs](https://gitbook.com/docs)

**GitBook's own docs, grounding the wiki's claims about how a hosted docs platform can sit over an OKF bundle: bidirectional Git Sync, change-request review, and features that serve the same content to AI/agents.**

## Summary
GitBook is a documentation platform that can be backed by a Git repository of
Markdown files and published as a searchable, navigable site. Its **Git Sync** is
bidirectional; its collaboration model uses **change requests** with review; and it
ships a set of AI/agent features (an Agent, an AI Assistant, an MCP server,
`llms.txt`, and `.md` export) that expose the same docs to machines.

## Key claims / quotes
- **Git Sync is bidirectional:** "Git Sync is bi-directional, so changes you make
  directly in GitBook's editor are automatically synced, as are any commits made on
  GitHub or GitLab." → [Presentation layer](../concepts/presentation-layer.md)
- Content is Markdown: Git Sync lets teams "turn a repo of Markdown files into
  beautiful, user-friendly docs." (Frontmatter/metadata preservation is not spelled
  out in the pages checked — treat the repo as authoritative for OKF metadata.)
- **Review workflow:** change requests enable team review before publication —
  a human sign-off gate.
- **AI/agent features:** a **GitBook Agent** ("drafts, edits, reviews change
  requests, and flags gaps"), an **AI Assistant** ("answers questions on your site
  from your docs"), **GitBook MCP** ("your published docs as a tool, so your
  customers' agents can read them properly"), an **`llms.txt`** documentation index,
  and **Markdown export** by appending `.md` to a page URL.
- A local **`skill.md`** can give an AI coding assistant context about GitBook.

## Why it matters here
GitBook is a concrete instance of a **[presentation layer](../concepts/presentation-layer.md)**
over an OKF bundle: the repo stays the compiled, attested source of truth while
GitBook renders it for humans and serves it to agents — the talk's "one architecture
[for] humans and Agents alike." Its bidirectional sync + change requests realise the
human half of [provenance and trust](../concepts/provenance-and-trust.md); its
MCP/`llms.txt` endpoints are an agent-access surface alongside [EduQuery](../entities/eduquery.md).

## Feeds
- [Presentation layer](../concepts/presentation-layer.md)
- [GitBook](../entities/gitbook.md)
