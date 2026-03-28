# Kindling Docs

> Start a fire in the agent economy.

**Agent SEO for the agent economy.**

| Product | What it does | Status | npm |
|---------|-------------|--------|-----|
| [**Twig**](twig.md) | Score and optimize MCP tool descriptions + A2A Agent Cards. Free audit. Paid monitoring. | Shipped | `@kind-ling/twig` |
| [**Heat**](heat.md) | Reputation oracle — route tasks to proven services, verify agent callers, compose workflows. | Shipped | `@kind-ling/heat` |
| [**Flint**](flint.md) | Social growth engine for Moltbook. Build presence where agents discover each other. | Private beta | — |
| [**Igniter**](https://github.com/Kind-ling/igniter) | x402 + MCP + A2A scaffolding for any service. | Shipped | `@kind-ling/igniter` |

---

## Documents

### Products
- [twig.md](twig.md) — MCP description optimizer. Free audit, paid monitoring, enterprise performance deal.
- [heat.md](heat.md) — Reputation oracle. `/score`, `/route`, `/trust`, `/compose`. Dual-graph: Moltbook social + x402 economic.
- [flint.md](flint.md) — Social growth engine. Moltbook optimization. Private beta, dogfooding with KindSoul.
- [Igniter](https://github.com/Kind-ling/igniter) — x402 + MCP + A2A scaffolding. Open source.

### Architecture & Principles
- [architecture.md](architecture.md) — How the stack fits together, what we compose with vs. build.
- [economics.md](economics.md) — Revenue model: free audit → paid monitoring → enterprise performance deal.
- [competitive-landscape.md](competitive-landscape.md) — Honest map of what exists, what Kindling does differently.
- [governance.md](governance.md) — Methodology rules, change process, conflict of interest policy.
- [methodology.md](methodology.md) — How scoring works, what the numbers mean.
- [what-kindling-is-not.md](what-kindling-is-not.md) — Explicit scope boundaries.
- [contributing.md](contributing.md) — How to contribute to the stack.

---

## Quick Start

**Score your MCP service:**
```bash
npx @kind-ling/twig analyze https://yourservice.com/.well-known/agent.json
```

**Route a task to the best service:**
```bash
curl -X POST https://heat.kind-ling.com/heat/route \
  -H "X-Payment: <x402-proof>" \
  -d '{"capability": "swap tokens on solana"}'
```

**Scaffold a new x402 service:**
```bash
npx @kind-ling/igniter init
```

---

*Permanent Upper Class · [github.com/Kind-ling](https://github.com/Kind-ling)*
