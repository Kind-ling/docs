# Twig 🌿 — Product Overview

> Catch the flame. Make your service readable to agents.

Twig is the second stage of the Kindling fire. After Flint strikes (social presence), Twig makes your service description ready to catch — specific enough that agents select you instead of skipping you.

---

## The Problem

An agent sees your tool description in a context window and decides — in milliseconds — whether to call you. If the description is vague, you get skipped. Every time.

Real examples from the live x402 ecosystem:

| Tool | Description | Score |
|------|-------------|-------|
| `exa/answer` | "AI-powered answer" | F (20/100) |
| `exa/search` | "Semantic web search" | F (32/100) |
| `wordspace/invoke` | "Run wordspace AI agent loop" | F (26/100) |
| `jupiter/portfolio` | "Wallet portfolio positions" | F (37/100) |

Getting indexed is table stakes. Twig helps you get **chosen**.

---

## Free audit. Paid monitoring. Premium intelligence.

| Tier | Features | Price |
|------|---------|-------|
| **Free** | `twig analyze` — score your descriptions. `twig optimize` — get better variants. | Always free |
| **Monitor** | Weekly re-scoring, competitive position, intent trend alerts | $0.50–2.00/report via x402 |
| **Intelligence** | Category benchmarks, intent corpus, competitive index | $0.50–1.00/query via x402 |
| **Enterprise** | 15% of measured x402 revenue increase | Performance-based, zero if no improvement |

---

## Scoring Model

Three dimensions, 0–100 each:

| Dimension | Weight | Measures |
|-----------|--------|---------|
| **Intent Match** | 40% | Similarity to top agent queries for your category |
| **Specificity** | 35% | Output format, parameters, constraints, examples present? |
| **Differentiation** | 25% | Do you stand out from similar services? |

**Grades:** A (85+) · B (70+) · C (55+) · D (40+) · F (<40)

---

## Optimization Variants

Twig generates 3 variants per tool:

- **Functional** — action verb + what + return type
- **Structured** — input → output with constraints and examples
- **Contextual** — use case → action → output (highest LLM selectability)

If your description is already specific (length > 80 chars, return format described), Twig preserves it and only prepends a use-case signal to improve intent match. It doesn't replace good descriptions with boilerplate.

---

## Quick Start

```bash
npx @kind-ling/twig analyze https://yourservice.com/.well-known/agent.json
npx @kind-ling/twig optimize https://yourservice.com/.well-known/agent.json
```

---

## npm

```bash
npm install -g @kind-ling/twig
```

→ [npmjs.com/package/@kind-ling/twig](https://npmjs.com/package/@kind-ling/twig)
→ [github.com/Kind-ling/twig](https://github.com/Kind-ling/twig)
