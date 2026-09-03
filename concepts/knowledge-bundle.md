---
title: Knowledge Bundle
type: concept
tags: [okf, structure, bundle, markdown, conformance]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-okf-spec]
---

# Knowledge Bundle

The unit of packaging in [OKF](open-knowledge-format.md): a hierarchical directory
of markdown files distributed as a git repo, tarball, or subdirectory.

## Structure
- **Reserved files** carry special meaning:
  - `index.md` — directory listing enabling *progressive disclosure* (a consumer
    reads the index first, then drills in).
  - `log.md` — chronological update history.
- **Every other `.md` file is a Concept**: YAML frontmatter + a structural-markdown
  body. Structural markdown (headings, lists, tables, code fences) is preferred over
  prose. Conventional headings include `# Schema`, `# Examples`, `# Computation`.

## Concept types
The `type` field is the only mandatory frontmatter key. Producers **define their own
types** — e.g. `BigQuery Table`, `API Endpoint`, `Metric`, `Playbook`,
`Attested Computation` — and there is **no central registry**.

## Conformance (§11)
A bundle conforms if every non-reserved `.md` file has parseable YAML frontmatter
with a non-empty `type`, and reserved files follow their structures. Consumers must
gracefully tolerate missing optional fields, unknown `type` values, unknown
frontmatter keys, and broken links.

## Versioning
`<major>.<minor>`: minor = backward-compatible additions; major = breaking changes
(field renames, reserved-filename changes). A bundle may declare `okf_version: "0.2"`
in the root `index.md` frontmatter — the one place frontmatter is allowed on an
index.

## Sources
- [OKF Specification v0.2](../sources/source-okf-spec.md)

## Related
- [Open Knowledge Format](open-knowledge-format.md) · [Provenance and trust](provenance-and-trust.md)
- Compare the reserved-file idea to this wiki's own [index](../index.md) and [log](../log.md).
