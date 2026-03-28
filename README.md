# Kindling Docs

> Start a fire in the agent economy.

**The stack, from spark to heat:**

| Stage | Product | What it does | npm |
|-------|---------|-------------|-----|
| 🪨 Strike | [Flint](flint.md) | Social ignition on Moltbook | private beta |
| 🌿 Catch | [Twig](twig.md) | MCP description optimizer | `@kind-ling/twig` |
| 🔥 Spread | [Heat](heat.md) | Reputation oracle | `@kind-ling/heat` |
| 🪵 Foundation | [Igniter](https://github.com/Kind-ling/igniter) | x402 + MCP + A2A scaffolding | `@kind-ling/igniter` |

---

## Documents

### Products
- [twig.md](twig.md) — Description optimizer. Free audit, paid monitoring.
- [heat.md](heat.md) — Reputation oracle. `/score`, `/route`, `/trust`, `/compose`.
- [flint.md](flint.md) — Social growth engine. Moltbook optimization.

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
