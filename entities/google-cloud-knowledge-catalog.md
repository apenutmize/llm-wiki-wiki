---
title: Google Cloud Knowledge Catalog
type: entity
tags: [tool, google-cloud, okf, catalog, agents]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-google-okf-blog, source-okf-spec]
---

# Google Cloud Knowledge Catalog

Google Cloud's catalog product and the home of the
[Open Knowledge Format](../concepts/open-knowledge-format.md) — the `knowledge-catalog`
repo hosts the OKF spec, and the catalog was updated to **ingest OKF bundles and
serve them to agents**.

## Relevance to this wiki
- Reference implementation of OKF as consumable infrastructure. Ships:
  - an **enrichment agent** that walks BigQuery datasets and drafts OKF documents,
  - a **static-HTML visualizer** with an interactive graph view (no backend),
  - sample bundles (GA4 e-commerce, Stack Overflow, Bitcoin).
- Demonstrates OKF's **producer/consumer independence**: the catalog is one
  consumer of a format any tool can read.

## Sources
- [Google Cloud — OKF blog](../sources/source-google-okf-blog.md)
- [OKF Specification v0.2](../sources/source-okf-spec.md)

_Stub._
