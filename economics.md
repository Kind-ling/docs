# Economics — Kindling

## Guiding principles

1. **Free audit, always.** The score is the hook. Seeing "F (28/100)" converts better than any pitch.
2. **Pay only for ongoing value.** Monitoring, intelligence, and competitive data are where we charge.
3. **Enterprise pricing is performance-based.** 15% of measured x402 increase. Zero if it doesn't work.
4. **Everything measured on-chain.** No self-reporting. No trust required.
5. **Referral splits cannot influence rankings.** Hard rule, enforced in code.

---

## Twig Revenue Model

### Free tier (always free)

| Feature | Description |
|---------|-------------|
| `twig analyze` | Score any MCP server or A2A Agent Card. See grade, issues, suggestions. |
| `twig optimize` | Generate 3 optimized description variants per tool. |
| Quickstart docs | Full documentation and methodology published. |

**Why free:** The audit reveals the problem. Seeing your service score F (28/100) is the conversion moment. No pitch needed.

### Paid tier — Continuous Monitoring

| Feature | Price | What you get |
|---------|-------|-------------|
| `twig monitor` | $0.50–2.00 per weekly report | Re-score weekly, diff vs. prior week, competitive position, intent trend alerts |
| `twig competitive` | $1.00 per query | Full category ranking — all services scored, you vs. the field |
| `twig intents` | $0.50 per category | Top agent queries this week, which services rank for each, gaps in coverage |

**Payment:** x402 on Base (USDC). Gated at request time.

**Why weekly monitoring:** Agent intent queries evolve. Competitors improve. Your score drifts. A score you earned in March may not hold in May. Monitoring catches drift before it becomes revenue loss.

### Enterprise tier — Performance-based

For services with measurable x402 volume, Kindling offers a performance deal:

- We optimize your descriptions
- You run them for 30 days
- We measure the delta using on-chain USDC transfer data
- You pay **15% of the revenue increase**
- Revenue flat or down? **Zero fee.**

**Who this is for:** Services with existing x402 volume looking to 2-5x their call rate. The on-chain measurement makes this verifiable and fair.

---

## Referral Economics (Igniter)

Igniter middleware includes an optional referral split mechanism for service operators who want to share revenue with referring agents or distribution partners.

**Hard rules:**
- Referral split percentage cannot influence service rankings in any Kindling product
- Referral relationships must be disclosed in every 402 response
- First-party services are labeled everywhere and lose ties
- Split size maximum: 30% of transaction value
- Default split if enabled: 15%

These rules exist because ranking manipulation via economics would destroy the signal value of Kindling's scoring. A service with better descriptions should rank higher than a service with bigger referral cuts.

---

## Heat Revenue Model

Heat is a reputation oracle with a free tier and paid tiers gated by x402 on Base.

| Endpoint | Price | What you get |
|----------|-------|-------------|
| `/heat/score` | Free (10/min) | 0–100 reputation score across 4 dimensions for any agent or service |
| `/heat/route` | $0.001/request | Ranked list of services for a given capability. 70% Heat + 30% Twig combined rank. |
| `/heat/trust` | $0.001/request | Trusted/untrusted verdict with confidence + sybil flags for an agent caller |
| `/heat/compose` | $0.005/request | Full ordered workflow for an intent — tool chain with cost estimates |

**Why the free `/score`:** Same principle as Twig — the score is the hook. An agent querying a service wants to know if it's trustworthy. Showing the score is free. Acting on it (routing, trust verification, workflow composition) costs micro-payments.

**Why `/compose` costs 5x more:** It's workflow intelligence, not just tool selection. It returns an ordered multi-step plan with expected costs, which requires combining social graph, economic graph, and Twig description data. Higher compute, higher value.

---

## Flint Revenue Model

Flint is not monetized in Phase 1. It is:

1. **Dogfood** — KindSoul proves it works
2. **Case study** — 4 weeks of honest before/after data
3. **Distribution** — KindSoul's Moltbook presence builds the audience for Twig

After the KindSoul case study, Flint pricing will be determined based on what actually drove engagement lift. Likely a monthly subscription per agent identity.

---

## Igniter Revenue Model

Igniter is open-source infrastructure. No direct monetization planned.

Its value to Kindling is ecosystem growth — more services using Igniter means more services to analyze with Twig. Every Igniter user is a potential Twig customer.

---

## Phase Gates

### Phase 1 exit criteria (before paid Twig features launch)
- 10 services analyzed with `twig analyze`
- 3 services deploy Twig-optimized descriptions
- 1 service pays for monitoring
- Methodology docs published and reviewed

### Phase 2 exit criteria (before enterprise deal)
- 5+ services on monitoring
- On-chain measurement validated against at least 2 services
- 30-day revenue delta measured and documented

---

## What "measured on-chain" means

Twig measures x402 revenue by querying USDC ERC-20 transfer logs on Base:

```
Base RPC → eth_getLogs → USDC contract → transfers TO wallet → sum values
```

Baseline = 7-day USDC received before optimization
Comparison = 7-day USDC received after optimization
Delta = difference
Fee = 15% of positive delta

No self-reporting. No API keys needed from the service operator. The chain is the source of truth.

**Current limitation:** This measures all USDC received, not only x402 payments. For services where x402 is the primary revenue source, this is accurate. For mixed-revenue services, a more granular measurement approach will be specified when needed.
