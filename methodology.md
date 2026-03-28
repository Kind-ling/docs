# Verifier Scoring Methodology v1.0

> Methodology is published before any scores. This document describes exactly how scores are computed. Anyone can reproduce a score from on-chain data using this specification.

**Version:** 1.0.0  
**Effective:** Published before first score emission  
**Next review:** 90 days after first score emission

---

## Scope: What this covers

**Heat** (shipped `@kind-ling/heat`) scores agents and services using a dual-graph model — Moltbook social graph + x402 economic graph. Heat scoring methodology is documented in [heat.md](heat.md).

**Verifier** (this document) is the deeper multi-dimensional scoring system for Kindling's future infrastructure modules — covering Demand, Reliability, and Outcome independently. Verifier ships after Phase 1 exit criteria are met.

If you're using Heat today, refer to [heat.md](heat.md). If you're contributing to or challenging Verifier methodology, you're in the right place.

---

---

## Three-Score Model

Scores are **never collapsed into a single number**. Three independent scores, each measuring a different dimension:

| Score | Data Source | Measures | Published When |
|-------|-------------|----------|----------------|
| **Demand** | On-chain x402 payments | Volume, unique payers, growth, frequency | After minimum thresholds met |
| **Reliability** | Uptime probes + telemetry (opt-in) | Latency, error rate, uptime, consistency | After minimum observation period |
| **Outcome** | Documenter benchmarks + community reports | Task accuracy, quality, correctness | After minimum benchmark samples |

Collapsing these into a composite score would obscure meaningful trade-offs (e.g., high demand + low reliability). Agents can weight dimensions according to their own priorities.

---

## Minimum Thresholds

Scores are **suppressed — not published** — until thresholds are met. Premature scores are worse than no scores.

| Score | Minimum to Publish | Below Threshold Display |
|-------|-------------------|------------------------|
| Demand | ≥10 unique paying wallets AND ≥30 transactions | "Insufficient data" |
| Reliability | ≥168 observation hours (7 days) AND ≥100 probed requests | "Insufficient data" |
| Outcome | ≥3 independent benchmark runs with published methodology | "Insufficient data" |

---

## Confidence Intervals

Every score is published as a **range, not a point estimate**:

```json
{
  "demand": {
    "value": 0.82,
    "confidence_interval": [0.76, 0.88],
    "sample_size": 87,
    "observation_window_days": 45
  }
}
```

Thin data = wide intervals. Wide intervals honestly communicate uncertainty. A score of `0.82 [0.40, 0.95]` means something very different from `0.82 [0.80, 0.84]`.

---

## Score Decay

Historical performance fades. Recent data is weighted more heavily.

| Score | Window | Decay |
|-------|--------|-------|
| Demand | 90-day rolling | >90 days: 50% weight; >180 days: 25% weight |
| Reliability | 30-day rolling | Infrastructure quality is current or irrelevant |
| Outcome | No decay | A published benchmark result is a permanent record. "Most recent benchmark" date is prominently displayed. |

---

## Demand Score

**Inputs:** On-chain x402 payment transactions to the service's registered wallet(s).

**Computation:**
1. Index all payments to registered wallets on supported chains (Base, others as adopted)
2. Apply decay weights based on transaction age
3. Count unique paying wallets (after entity resolution and self-traffic exclusion)
4. Compute normalized score: `f(volume, unique_payers, growth_rate, frequency)`
5. Apply confidence interval based on sample size

**Exclusions:**
- Self-traffic (affiliated wallet payments)
- Payments from wallets created <7 days before first payment (25% weight, not full exclusion)
- Burst payments: >10 from single wallet in <60 seconds (flagged, reviewed)
- Payments with `referral_split_pct > 50%` are excluded from normalization (counted in raw volume, not normalized score)

---

## Reliability Score

**Inputs:** Synthetic uptime probes (Kindling infrastructure) + opt-in telemetry from service operators.

**Computation:**
1. Probe registered endpoints at randomized intervals (minimum every 5 minutes)
2. Measure: response time, HTTP status, response validity
3. Compute: uptime %, p50/p95/p99 latency, error rate
4. Normalize to 0–1 score
5. Apply 30-day rolling window

**Opt-in telemetry:** Services can provide richer data (internal latency, queue depth, etc.) via Igniter telemetry hooks. This data is disclosed in Verifier output.

---

## Outcome Score

**Inputs:** Documenter benchmark reports + community-submitted benchmark results.

**Requirements for a valid benchmark:**
- Methodology published before results
- Minimum 3 independent runs
- Competitor services included (not just the service being evaluated)
- Raw data published alongside report

**Computation:**
- Aggregate task accuracy across benchmark runs
- Weight by benchmark recency (most recent prominently displayed; no decay on historical records)
- Flag if all benchmarks are from a single source

---

## Entity Resolution

The hardest problem in on-chain reputation.

| Case | Policy |
|------|--------|
| Default | One wallet = one entity. No cross-wallet linking without explicit registration. |
| Voluntary linking | Services register multiple wallets via signed attestation. Combined data for scoring, disclosed in output. |
| Cross-chain | Services on multiple chains register all wallets. Scores computed per-chain, combined only if explicitly linked. |
| Custodial settlement | Payments through exchanges/processors flagged. Excluded from unique-payer counts unless provider gives wallet-level attribution. |

---

## Anti-Sybil Measures

| Measure | Implementation |
|---------|---------------|
| Wallet age weighting | Wallets created <7 days before first payment receive 25% weight |
| Burst detection | >10 payments from single wallet in <60 seconds: flagged for review |
| Diversity threshold | Demand score requires ≥10 unique payers; below = suppressed |
| Pattern matching | Regular micro-payments at fixed intervals from single source: flagged |
| Affiliated wallet disclosure | Services must disclose wallets they control; self-traffic labeled, excluded from unique-payer count |

---

## Methodology Versioning

- Every change is versioned: `methodology-{semver}`
- Changes announced minimum **7 days before enforcement**
- Historical scores preserved under their original methodology version
- Changelog includes rationale for every change
- Anyone can compute scores from on-chain data using published methodology

### Change Process

1. Proposed change published with rationale
2. 7-day public comment period
3. Change takes effect (or is revised based on feedback)
4. Changelog updated
5. Historical scores annotated with methodology version

---

## Reproducibility

The goal: anyone can independently compute a Verifier score using:
1. This methodology document
2. On-chain data (publicly available)
3. The probe data (published with scores)

If a score cannot be reproduced from published data, that is a methodology bug. File a challenge.

---

*Methodology v1.0.0 · Kindling Verifier · Permanent Upper Class · March 2026*
