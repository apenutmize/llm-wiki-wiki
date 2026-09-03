---
title: Attested Computation
type: concept
tags: [okf, attestation, verification, computation, trust]
status: draft
created: 2026-09-02
updated: 2026-09-02
sources: [source-okf-spec]
---

# Attested Computation

A dedicated [OKF](open-knowledge-format.md) concept type
(`type: Attested Computation`) that encodes a **sanctioned way to compute a value**,
so a consumer can verify the value came from a blessed procedure rather than
improvised SQL or a hallucinated number.

## Key fields
- `runtime` — e.g. `bigquery | postgres | dbt | python`.
- `parameters` — declared `{ name, type, required }`; the agent may supply values
  but **cannot edit the computation itself**.
- `computation` — path to the SQL/code file (or an inline fenced block under a
  `# Computation` heading).
- `executor` — run instructions plus the `receipt` fields returned.
- `attester` — deterministic verification code.

## Consumer workflow
1. **Discover** via type/frontmatter.
2. **Load** the contract and computation.
3. **Parameterize** with declared values only.
4. **Execute** via the executor, collecting a receipt.
5. **Attest**: consumer-side verification confirms the sanctioned computation ran —
   not a rewritten query.
6. **Gate**: refuse to display failed attestations; warn if stale.

## Why it matters here
It extends [provenance and trust](provenance-and-trust.md) from *"who wrote this"*
to *"was this number actually produced the sanctioned way"*. For a knowledge base
that feeds agents, this is a strong mitigation of the
[hallucination-baking risk](hallucination-baking-risk.md): a computed claim can be
re-executed and checked, not just believed.

## Sources
- [OKF Specification v0.2](../sources/source-okf-spec.md)

## Related
- [Provenance and trust](provenance-and-trust.md) · [Open Knowledge Format](open-knowledge-format.md)
