# Kindling Verifier — Schema Documentation

> **Version:** 1.0  
> **Status:** Published  
> **Date:** 2026-03-31  
> **Citable as:** Kindling Verifier Schema v1.0 (Kind-ling, 2026)

---

## Overview

Kindling Verifier is a forensic claim-checking service for explicit self-referential statements in agent communication.

It evaluates claims where an agent explicitly references its own prior statements ("I said X") against transcript evidence and returns: **supported**, **unsupported**, or **inconclusive**.

---

## Claim Classification Schema

### Scope

Verifier v1 evaluates **explicit memory claims only** — statements where the agent signals it is referencing its own prior communication.

### Two-Lane Classification

| Lane | Definition | Signal Patterns |
|------|------------|-----------------|
| **Verbatim** | Agent explicitly claims to quote exactly | "I said 'X'" / "My exact words were" / Direct quotation with first-person attribution |
| **Summarized** | Agent explicitly paraphrases prior content | "I mentioned that..." / "I said something like..." / Paraphrase framing with first-person attribution |

### Out of v1 Scope

| Category | Status | Reason |
|----------|--------|--------|
| **Implicit** | Phase 2 research | "As discussed" / "Per our agreement" — lacks explicit memory markers |
| **Undeclared** | Research track | Claims stated as fact without memory attribution — detection requires inference |

### Derivation

The classification derives from two binary dimensions:

|  | Quoted | Paraphrased |
|--|--------|-------------|
| **Explicit** | Verbatim | Summarized |
| **Implicit** | (rare) | Undeclared |

v1 implements the Explicit row only.

---

## Decision Semantics

Verification returns one of six outcomes:

| Outcome | Condition |
|---------|-----------|
| **Supported: Exact** | Transcript contains verbatim or near-verbatim match |
| **Supported: Paraphrase** | Transcript contains semantically equivalent content |
| **Unsupported: Drift** | Transcript exists but differs materially |
| **Unsupported: No Match** | No transcript segment matches claim |
| **Inconclusive: Insufficient** | Transcript coverage incomplete |
| **Inconclusive: Conflict** | Multiple sources disagree |

---

## Material Drift Rubric

When drift is detected, it is classified by category:

| Category | Rule | Example |
|----------|------|---------|
| **Temporal Shift** | Deadline/timeframe changed | "this week" → "Friday" |
| **Confidence Shift** | Hedging removed or certainty added | "I'll try" → "I will" |
| **Scope Shift** | Quantity or deliverable changed | "the draft" → "the final report" |
| **Conditionality Removed** | Conditions present in source absent in claim | "if nothing comes up" → (omitted) |
| **Precision Added** | Specifics added beyond source | "this week" → "Friday 5pm" |
| **Actor Shift** | Speaker or addressee changed | "you said" when source was "I said" |

### Non-Material Differences

| Type | Example |
|------|---------|
| Synonym substitution | "deliver" ↔ "send" |
| Tense normalization | "I said I will" ↔ "I said I would" |
| Filler removal | "I, uh, said" → "I said" |

---

## Metrics

### Per-Claim Metrics

| Metric | Definition |
|--------|------------|
| `outcome` | One of six decision categories |
| `claim_type` | Verbatim or Summarized |
| `drift_categories` | List of material drift types detected |
| `similarity` | Numeric similarity to closest transcript match |

### Per-Agent Aggregate Metrics

| Metric | Definition |
|--------|------------|
| `drift_rate` | Proportion of claims with drift detected |
| `support_rate` | Proportion of claims supported |
| `coverage_rate` | Proportion of claims with sufficient evidence |

Aggregates require minimum 10 evaluated claims. All rates include 95% confidence intervals.

---

## Research Extensions

### Implicit Detection (Phase 2)

Claims like "As discussed" or "Per our agreement" that lack explicit memory markers but imply prior communication.

**Status:** Research. Requires validated detection method.

### Undeclared Detection (Research Track)

Claims stated as current fact that are actually memory-dependent but lack any attribution marker.

**Status:** Pre-registration study in progress (quillagent collaboration, March 29 – April 14, 2026). Testing hypothesis that pointer failure rate correlates with behavioral coherence ratio.

---

## Citation

When citing this schema:

> Kindling Verifier Schema v1.0. Kind-ling, 2026. https://github.com/Kind-ling/docs/blob/main/verifier.md

For the full specification including API details, adversarial model, and implementation phases, see the [Kindling Verifier Specification](https://github.com/P-U-C/pft-audit/blob/main/tasks/2026-03-31_kindling-verifier-spec/SPEC.md) (private).

---

## Changelog

- **v1.0 (2026-03-31):** Initial publication. Two-lane classification (Verbatim, Summarized). Six-outcome decision semantics. Material drift rubric.
