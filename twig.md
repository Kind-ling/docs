# Twig — Product Overview

> Agents choose you or they don't. Twig makes them choose you.

---

## What Twig is

A CLI tool that scores MCP tool descriptions and A2A Agent Card skills, then generates optimized variants. Revenue model: 15% of measured x402 revenue increase. Pay nothing if it doesn't work.

---

## The Problem

Every MCP tool has a description. That description is what an LLM reads when deciding whether to call your service.

Most descriptions are written by developers who know their tool intimately — which means the descriptions describe implementation, not capability. They tell agents what a tool *is*, not what it *does for them*.

**Real examples from the x402 ecosystem:**

| Service | Current `llm_usage_prompt` |
|---------|---------------------------|
| `exa/answer` | "AI-powered answer" |
| `wordspace/invoke` | "Run wordspace AI agent loop" |
| `exa/find-similar` | "Find similar pages" |
| `x402 Payment Harness` | "To use x402 Payment Harness, call https://github.com/rplryan/x402-payment-harness with x402 payment of 0.0 USDC. Send json input. Returns json. Description: Python library for x402 payment flows." |

These tools are useful. Their descriptions are not. The tools that win are the ones that tell agents exactly what they'll get.

---

## Scoring Model

Three dimensions, 0–100 each:

| Dimension | Weight | What it measures |
|-----------|--------|-----------------|
| **Intent Match** | 40% | Cosine similarity to top-50 agent queries for this tool's category |
| **Specificity** | 35% | Output format, input params, constraints, examples present? |
| **Differentiation** | 25% | Embedding distance from cluster centroid of similar services |

**Composite** = weighted average. Grades: A (85+), B (70+), C (55+), D (40+), F (<40).

Score below 40 = agents are probably skipping you.

---

## Optimization Engine

For each tool scoring below 70, Twig generates 3 variants:

1. **Functional** — action verb + subject + return type
2. **Structured** — input → output with constraints and examples
3. **Contextual** — use case → action → output (optimizes for LLM selection)

Each variant is scored on all 3 dimensions. Developer reviews and picks.

---

## Revenue Model

Twig is free to analyze. Optimization is free. We charge **15% of measured x402 revenue increase**, paid in USDC on Base.

- Set a baseline before optimization: `twig measure <wallet> --baseline`
- Deploy new descriptions
- Run for 14–30 days
- Compare: `twig measure <wallet> --compare`
- Revenue up? Pay 15% of the delta. Revenue flat or down? Pay nothing.

Everything measured on-chain. No self-reporting. No trust required.

---

## Non-goals

Twig does NOT:
- Replace MCPay as a payment router
- Replace x402-discovery as a service index
- Replace ERC-8004 as an identity standard
- Rank services (that's what Kindling Hub will do)

Twig composes with all of these. It is strictly an optimization layer.

---

## CLI Reference

```bash
# Score current descriptions
twig analyze https://myservice.com/.well-known/agent.json

# Generate optimized variants
twig optimize https://myservice.com/.well-known/agent.json

# Set revenue baseline
twig measure 0xWallet --baseline

# Compare after deploying new descriptions
twig measure 0xWallet --compare

# Full revenue report
twig report 0xWallet --period 30d
```

---

## Repo

[github.com/Kind-ling/twig](https://github.com/Kind-ling/twig)
