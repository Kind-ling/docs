# Architecture

> Each module provides standalone value. Together, they create reinforcing loops.

---

## Module Relationships

```
┌─────────────────────────────────────────────────────────────┐
│  Service Developer                                           │
│                                                             │
│  npx @kindling/igniter init                                 │
│       │                                                     │
│       ▼                                                     │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  Kindling Igniter (Phase 1)                         │   │
│  │                                                     │   │
│  │  x402 middleware  →  402 response with economics   │   │
│  │  A2A generator    →  /.well-known/agent.json        │   │
│  │  MCP wrapper      →  tool definitions               │   │
│  └──────────────────────────┬──────────────────────────┘   │
│                             │ on-chain payments             │
└─────────────────────────────┼───────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Base Mainnet (x402 settlements)                            │
│                                                             │
│  Payment transactions  →  Kindling Verifier indexer         │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│  Kindling Verifier (Phase 1 → Phase 2)                      │
│                                                             │
│  Phase 1: Demand scores only (on-chain payment data)        │
│  Phase 2: + Reliability (probes) + Outcome (benchmarks)     │
│                                                             │
│  Output: { demand, reliability, outcome }                   │
│          each with confidence_interval + sample_size        │
│          is_first_party flag on all PUC services            │
└──────────────────────────────┬──────────────────────────────┘
                               │
              ┌────────────────┴────────────────┐
              │                                 │
              ▼                                 ▼
┌─────────────────────────┐   ┌─────────────────────────────┐
│  Kindling Documenter    │   │  Kindling Scout              │
│  (Phase 2)              │   │  (Phase 3)                   │
│                         │   │                              │
│  Benchmark reports      │   │  Task routing engine         │
│  Published methodology  │   │  Referral economics          │
│  Raw data included      │   │  Audit log                   │
│  Competitors included   │   │  Self-hostable               │
└─────────────────────────┘   └─────────────────────────────┘
```

---

## Data Flows

### Igniter → Chain → Verifier

1. Service installs Kindling Igniter
2. Agent calls service, receives 402 with payment details + referral disclosure
3. Agent pays via x402, settlement lands on Base
4. Verifier indexes the payment transaction
5. Payment contributes to service's Demand score (after thresholds met)

### Verifier → Scout

1. Scout queries Verifier for candidate services
2. Verifier returns scores with `is_first_party` flags
3. Scout applies routing policy: eligibility → quality floor → agent preferences → economics → first-party tie-break
4. Scout logs decision factors for auditability

### Verifier → Documenter

1. Documenter runs benchmarks against services indexed by Verifier
2. Results published with raw data + methodology
3. Outcome scores feed back into Verifier (Phase 2)

---

## Stack

| Layer | Technology | Notes |
|-------|-----------|-------|
| Payment | x402 / HTTP 402 | Chain: Base (primary), configurable |
| Agent discovery | MCP + A2A | Tool definitions + Agent Cards |
| Identity | ERC-8004 | Optional but encouraged for trust signals |
| Indexing | Custom indexer | Base mainnet RPC, open-source |
| Scoring | TypeScript service | Deployed by PUC, reproducible locally |
| Storage | PostgreSQL + on-chain | Scores in DB; payment proofs on-chain |
| APIs | REST + MCP server | Verifier queryable by agents directly |

---

## Phase Dependencies

```
Phase 1 (Foundation)
├── Igniter: x402 + A2A + MCP scaffolding
└── Verifier: demand scores from on-chain data

Phase 2 (Credibility) — requires Phase 1 exit criteria
├── Verifier: + reliability + outcome scores
└── Documenter: benchmark engine

Phase 3 (Routing) — requires Phase 2 exit criteria + 60 days data + 20 services
└── Scout: task routing + referral economics

Phase 4 (Aggregator) — requires 50 services + demonstrated routing differentiation
└── Deploy only if preconditions met
```

---

## Self-Hosting

Every module is self-hostable:

- **Igniter**: npm/pip package, runs in your process
- **Verifier**: Docker image + indexer, points at any Base RPC
- **Scout**: Standalone router, can run without managed Scout service

The managed Scout service (Phase 3) is optional. Agents can bypass it and query Verifier directly.

---

*Architecture v1.0 · Kindling · March 2026*
