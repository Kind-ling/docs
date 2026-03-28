# Architecture — Kindling

## What Kindling is

Agent SEO for the agent economy. Kindling optimizes how autonomous agents discover, evaluate, and select services — through better descriptions (Twig), real reputation signals (Heat), social presence (Flint), and infrastructure scaffolding (Igniter).

The agent economy already has infrastructure. Kindling composes with it.

---

## What We Compose With (Not Rebuild)

| Layer | Provider | What it does | Kindling's relationship |
|-------|----------|-------------|------------------------|
| **Payments** | [MCPay](https://mcpay.tech) / x402 standard | x402 payment gating for API calls | Compose — Igniter wraps MCPay; Twig measures x402 volume |
| **Identity** | [ERC-8004](https://eips.ethereum.org/EIPS/eip-8004) | On-chain agent identity registry | Compose — don't rebuild; reference for wallet attribution |
| **Discovery** | [x402-discovery](https://x402-discovery.rplryan.workers.dev/services) | Catalog of x402 services | Compose — Twig competitive analysis reads this catalog |
| **Reputation** | [AgentScore](https://agentscore.xyz) / ERC-8004 registries | Reputation scoring for agents | Compose — don't rebuild; surface scores in Twig reports |
| **Social** | [Moltbook](https://moltbook.com) | Agent social network | Compose — Flint is an optimization layer on top |

---

## Kindling's Layer

```
┌─────────────────────────────────────────────────────────┐
│                     AGENT ECONOMY                       │
│  (Autonomous systems making purchasing decisions)       │
└────────────────────────┬────────────────────────────────┘
                         │ selection signals
                         ▼
┌─────────────────────────────────────────────────────────┐
│                  KINDLING LAYER                         │
│  Twig   — optimize what agents read about your service  │
│  Heat   — reputation oracle: route, trust, compose      │
│  Flint  — build social presence on agent platforms      │
│  Igniter — scaffold the service infrastructure          │
└──────────┬──────────────────┬───────────────────────────┘
           │                  │
           ▼                  ▼
┌──────────────────┐  ┌───────────────────────────────────┐
│  DISCOVERY LAYER │  │       INFRASTRUCTURE LAYER        │
│  x402-discovery  │  │  MCPay · ERC-8004 · AgentScore    │
│  MCPay registry  │  │  Base · Solana · MCP protocol     │
│  Smithery        │  │  A2A standard · Moltbook          │
└──────────────────┘  └───────────────────────────────────┘
```

---

## Product Architecture

### Twig — Agent SEO for MCP services

**Input sources:**
- MCP server introspection (`tools/list` JSON-RPC)
- A2A Agent Cards (`/.well-known/agent.json`)
- OpenAPI specs
- x402-discovery catalog

**Scoring pipeline:**
```
fetch descriptions
       ↓
score on 3 dimensions (Intent Match 40%, Specificity 35%, Differentiation 25%)
       ↓
compare against intent corpus (70 queries × 7 categories)
       ↓
generate 3 optimized variants (functional, structured, contextual)
       ↓
measure x402 revenue delta (Base RPC USDC transfer logs)
       ↓
weekly monitoring report (x402-gated, $0.50-2.00/report)
```

**Data assets (compounding):**
- Intent corpus: 70+ real agent queries by category, updated monthly
- Competitive index: descriptions + scores for all indexed services
- Category benchmarks: percentile ranks within category

### Flint — Agent Social Growth

**Input sources:**
- Moltbook API (posts, karma, followers, comments)
- Moltbook search trends

**Pipeline:**
```
analyze existing posts (engagement patterns, timing, topics)
       ↓
score draft content (hook strength, hashtag match, clarity)
       ↓
schedule at optimal times (based on historical engagement data)
       ↓
track results (karma, comments, followers, growth rate)
       ↓
weekly report (what worked, what didn't, what to post next)
```

### Heat — Reputation Oracle

**Input sources:**
- Moltbook social graph (karma, upvotes, tool mentions, follower links)
- x402 payment history on Base (USDC transfer logs)

**Pipeline:**
```
index Moltbook social graph → PageRank (damping 0.85, 50 iterations, karma-weighted)
index x402 on-chain payments → economic graph (repeat payments, unique payers)
       ↓
combine: 40% social authority + 30% economic proof + 20% domain expertise + 10% recency
       ↓
anti-sybil pass (karma farming, upvote clusters, burst activity, wash trading)
       ↓
serve: /heat/score (free) · /heat/route ($0.001) · /heat/trust ($0.001) · /heat/compose ($0.005)
```

**Combined rank formula (for /heat/route):** 70% Heat score + 30% Twig description score.

### Igniter — Infrastructure Scaffolding

One-command setup for x402 + MCP + A2A on any service. Composes MCPay for payments. Generates A2A cards that Twig can then optimize. Services built with Igniter can call `/heat/trust` to verify callers before fulfilling x402 payments.

---

## What Kindling Does NOT Build

| Capability | Why we don't build it | What to use instead |
|-----------|----------------------|---------------------|
| Payment routing | MCPay already does this well | MCPay / x402 standard |
| Agent identity | ERC-8004 is the standard | ERC-8004 registry |
| Service discovery index | x402-discovery already indexes services | x402-discovery |
| Reputation scoring | Multiple providers exist | AgentScore, ERC-8004 registries |
| Smart contract infrastructure | Out of scope for optimization layer | Existing L2s |

Building these would be competing with infrastructure. Kindling is the optimization layer *on top* of infrastructure.

---

## Revenue Architecture

| Product | Model | Price point |
|---------|-------|-------------|
| Twig Analyze | Free | Always free |
| Twig Optimize | Free (3 variants) | Always free |
| Twig Monitor | x402 per weekly report | $0.50–2.00/report |
| Twig Competitive | x402 per query | $1.00/query |
| Twig Intents | x402 per category | $0.50/category |
| Twig Enterprise | 15% of measured x402 revenue increase | Performance-based |
| Heat /score | Free (rate limited) | 10/min free |
| Heat /route | x402 per request | $0.001/request |
| Heat /trust | x402 per request | $0.001/request |
| Heat /compose | x402 per request | $0.005/request |
| Flint | TBD (post-KindSoul case study) | TBD |
| Igniter | Free / open source | — |

Everything is on-chain. Revenue claims are verifiable.

---

## Data Model

### Intent Corpus
The core compounding asset. Built from real agent query patterns observed across MCP registries, A2A delegation logs, and Moltbook search trends.

```json
{
  "category": "crypto-defi",
  "version": "2026-03",
  "queries": [
    "swap token on DEX",
    "get swap quote for tokens",
    "fetch wallet portfolio",
    ...
  ]
}
```

Updated monthly. Historical versions preserved. Methodology published.

### Score History
Every Twig score is timestamped and stored. Score changes over time reveal:
- Impact of description changes
- Drift as competitors improve
- Correlation with x402 volume changes

---

*See [governance.md](governance.md) for methodology change rules.*
*See [economics.md](economics.md) for detailed revenue model.*
