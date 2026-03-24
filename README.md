# Kindling

> Open infrastructure for the agent economy.

Kindling is a set of open-source modules that make it easy to build, discover, evaluate, and pay for agent-native services. Each module is independently useful. Together, they create reinforcing loops across MCP, A2A, and x402.

**Built by [Permanent Upper Class](https://permanentupperclass.com). Economics are on-chain and auditable.**

---

## Thesis

Agent adoption is a **configuration and selection decision**, not a marketing funnel.

Five protocol-level mechanisms determine how AI agents discover, evaluate, adopt, and propagate information about services:

1. **MCP tool descriptions** — what agents see when choosing tools
2. **A2A Agent Cards** — machine-readable capability declarations
3. **x402 settlement** — payment, discovery, and onboarding in one HTTP exchange
4. **Context window content** — what gets passed between agents
5. **On-chain transaction history** — verifiable demand and reputation signals

Crypto is non-optional for machine-to-machine commerce. x402 collapses discovery, payment, and onboarding into a single HTTP exchange. On-chain settlement creates verifiable demand and reputation signals that fiat rails cannot provide.

The connective infrastructure layer — reputation scoring, quality benchmarking, developer tooling, task routing — is unoccupied. Kindling occupies it with open-source modules that each provide standalone value and, when composed, create reinforcing loops across all five mechanisms.

PUC operates both the infrastructure and services that participate in it. This is **disclosed everywhere** and governed by explicit anti-self-preferencing policies. See [governance.md](./governance.md).

---

## Modules

| Module | Package | Phase | Status | Description |
|--------|---------|-------|--------|-------------|
| **[Kindling Igniter](https://github.com/Kind-ling/igniter)** | `@kindling/igniter` / `kindling-igniter` | 1 | 🟠 Building | x402 + MCP + A2A scaffolding for any service |
| **Kindling Verifier** | `@kindling/verifier` | 1 | 🔵 Planned | Multidimensional reputation scoring (Demand · Reliability · Outcome) |
| **Kindling Documenter** | `@kindling/documenter` | 2 | 🔵 Planned | Benchmark engine with published methodology and raw data |
| **Kindling Scout** | `@kindling/scout` | 3 | 🔵 Planned | Agent task routing with referral economics |

**Phase 2 ships only if Phase 1 exit criteria are met. Phase 3 ships only if Phase 2 exit criteria are met.**

---

## What Kindling Is Not

See [what-kindling-is-not.md](./what-kindling-is-not.md) for the full list. Short version:

- Not a closed marketplace
- Not pay-to-rank
- Not hidden affiliate routing
- Not benchmark theater
- Not first-party self-preferencing dressed as infrastructure

---

## Docs

| Document | Description |
|----------|-------------|
| [governance.md](./governance.md) | Conflict policy, anti-self-preferencing, advisory review |
| [economics.md](./economics.md) | Referral mechanics, split rules, self-traffic policy |
| [methodology.md](./methodology.md) | Verifier scoring methodology v1.0 |
| [architecture.md](./architecture.md) | Module relationships and data flows |
| [what-kindling-is-not.md](./what-kindling-is-not.md) | Scope boundaries |
| [contributing.md](./contributing.md) | How to contribute |

---

## Quick Start

```bash
npx @kindling/igniter init
```

Generates x402 middleware, A2A Agent Card, and MCP server wrapper for your service in under 5 minutes.

---

*Kindling v1.1 · Permanent Upper Class · @zozDOTeth · March 2026*
