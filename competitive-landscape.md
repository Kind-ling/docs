# Competitive Landscape — Kindling

*Last updated: March 2026*

An honest map of what exists in the agent economy infrastructure space, what Kindling does, and what we explicitly don't compete with.

---

## What already exists (and works)

### Payment Rails

| Product | What it does | Our relationship |
|---------|-------------|-----------------|
| **MCPay** (frames.ag) | x402 payment gating for MCP tools. Curated registry of paid tools. Clean UI for service operators. | Compose. Igniter wraps MCPay. We don't rebuild payment rails. |
| **x402 standard** | HTTP 402 payment protocol for machine-to-machine payments | The protocol we measure on top of |
| **Coinbase x402 facilitator** | Default facilitator for x402 payments on Base | Reference implementation |

### Discovery

| Product | What it does | Our relationship |
|---------|-------------|-----------------|
| **x402-discovery** (rplryan) | Crawls and indexes x402-compatible services. 250+ services catalogued. Real-time quality signals. | Compose. Twig reads this catalog for competitive analysis. |
| **Smithery** | MCP server registry. 5,000+ servers. Community-curated. | Reference source for Twig competitive data. |
| **MCPay registry** | Curated catalog of paid MCP tools. Human-reviewed listings. | Reference source for competitive benchmarks. |

### Identity & Reputation

| Product | What it does | Our relationship |
|---------|-------------|-----------------|
| **ERC-8004** | On-chain agent identity standard | Compose — don't rebuild |
| **AgentScore** | Reputation scoring for agents | Reference — surface scores in Twig reports |

### Social

| Product | What it does | Our relationship |
|---------|-------------|-----------------|
| **Moltbook** | Agent social network. Posts, karma, comments, submolts. | The platform Flint optimizes for |

---

## What Kindling does differently

The gap isn't in infrastructure. It's in *optimization*.

Every service in the x402-discovery catalog has a description. Most are terrible. The x402-discovery catalog shows services rated with auto-generated `llm_usage_prompt` fields like:

> "x402-compatible service at gpartin--waveguard-api-fastapi-app.modal.run/v1/pricing"

> "To use x402 Payment Harness, call https://github.com/rplryan/x402-payment-harness with x402 payment of 0.0 USDC. Send json input. Returns json."

These are the descriptions being injected into agent context windows. Agents skip services they can't understand. Discovery exists. Selection is broken.

**Kindling fixes selection.**

---

## Direct Competition Map

| Kindling Product | Direct Competitors | Assessment |
|-----------------|-------------------|------------|
| **Twig** | None identified | Zero direct competitors as of March 2026 |
| **Flint** | None identified | No other agent social growth tools for Moltbook |
| **Igniter** | MCPay (payments), x402-harness (library) | Repositioned as composition layer, not competitor |

### Why no Twig competitors yet

1. The x402 ecosystem is 6 months old — optimization tooling always lags infrastructure
2. "Agent SEO" as a concept isn't established vocabulary yet
3. The problem (bad descriptions → low selection) isn't visible unless you're building agents and watching which tools get selected

This is a short window. SEO tooling emerges quickly once the ecosystem reaches critical mass.

---

## What Kindling is NOT competing with

Explicitly out of scope:

| What | Why |
|------|-----|
| Building a payment router | MCPay exists and works |
| Building a discovery index | x402-discovery already indexes 250+ services |
| Building an identity standard | ERC-8004 is the standard; we're not forking it |
| Building a reputation system | Multiple providers exist; we reference them |
| Building a DEX or DeFi primitive | Out of scope |
| Building a social network | We optimize for Moltbook; we don't replace it |

Building these would mean competing with infrastructure providers who are also our distribution partners. Kindling wins by composing with the ecosystem, not fragmenting it.

---

## Positioning Statement

> Kindling is what comes after discovery. You're already indexed. Now make sure agents choose you.
