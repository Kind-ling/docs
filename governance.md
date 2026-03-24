# Governance & Conflict Policy

> Kindling is trustworthy not because PUC promises neutrality, but because the system minimizes discretionary power: methodology is public, rankings are reproducible, first-party inventory is labeled, routing decisions are exportable and explainable, and services can self-host or bypass any module entirely.

---

## The Core Problem

Permanent Upper Class (PUC) operates both Kindling infrastructure and services that participate in it. This conflict of interest is **real and permanent**. It is managed through structural constraints, not promises.

---

## Anti-Self-Preferencing Policy

| Commitment | Implementation |
|-----------|---------------|
| First-party services are always labeled | `is_first_party: true` in Verifier responses, Scout routing logs, Documenter reports, and Agent Cards |
| No scoring adjustments for first-party | Same methodology, same thresholds, same decay — no exceptions |
| First-party loses ties | If two services are equivalent on all scoring dimensions, the non-first-party service wins. First-party wins only if measurably superior or the agent explicitly prefers first-party. |
| Referral splits cannot influence ranking | Hard rule enforced in Scout routing code. Split size is disclosed but has zero effect on position. |
| Documenter includes competitor wins | Reports that don't include competitor advantages are not published. Losses are shown. |
| Methodology changes announced before enforcement | Minimum 7-day public notice before any methodology change takes effect. |
| Raw data always published | Every Verifier score and Documenter benchmark includes the data needed to reproduce it independently. |

---

## Transparency Commitments

- **Rankings are explainable**: methodology + data + computation = reproducible score
- **Routing is auditable**: Scout logs candidates, scores, selection factors, and first-party flags
- **Services opt in/out freely**: no lock-in, no penalty for leaving
- **All wallets disclosed**: ownership attested under this governance policy
- **Governance docs published before any module ships**: trust is established before code

---

## Advisory Review

Quarterly review by independent ecosystem participants.

| Parameter | Value |
|-----------|-------|
| Frequency | Quarterly |
| Minimum reviewers | 3 independent ecosystem participants (disclosed by name) |
| Scope | Methodology changes, dispute resolutions, self-preferencing allegations |
| Authority | Recommendation authority (not veto power) |
| Publication | All recommendations and PUC responses are published publicly |

Advisory board members are disclosed. Their recommendations and PUC's responses are published regardless of outcome.

---

## Wallet Governance

| Rule | Detail |
|------|--------|
| Distinct wallets per product | Kindling infrastructure, b1e55ed, and other PUC services each have separate disclosed wallets |
| Multisig where feasible | Treasury and high-value operational wallets use multisig |
| Rotation notice | 30-day public notice before any wallet rotation or migration |
| Attestation | Wallet ownership is attested via signed message, published in this repo |

### Disclosed PUC Wallets

| Purpose | Address | Attested |
|---------|---------|---------|
| Kindling referral recipient | TBD — published before Phase 1 launch | — |
| b1e55ed oracle | `0xb1e55edd3176ce9c9af28f15b79e0c0eb8fe51aa` | ✓ |
| PUC treasury | TBD | — |

---

## Challenge Process

Any entity can challenge a Verifier score or Documenter benchmark result.

| Step | Detail |
|------|--------|
| Who can file | Any indexed service, or any entity with evidence of scoring error |
| Required evidence | Specific score disputed, methodology section in question, supporting data |
| Initial response | Within 72 hours |
| Resolution | Within 14 days |
| Status during dispute | Score annotated "under review" — not removed |
| Resolution publication | Documented publicly regardless of outcome. Methodology updated if gap confirmed. Past scores amended or superseded with explanation. |
| Appeal | If resolution unsatisfactory, advisory board review at next quarterly cycle |

---

## Self-Traffic Policy

- Services **must disclose** wallets they control
- Payments between affiliated wallets are labeled `self_traffic: true`
- Self-traffic is **excluded** from Verifier demand score unique-payer counts
- Self-traffic volume is displayed separately — not hidden, not penalized, just labeled

---

## What Happens If These Rules Are Broken

If credible evidence of self-dealing survives investigation:

1. Affected scores are retracted and annotated
2. Methodology is updated to close the gap
3. Public post-mortem is published
4. Advisory board reviews structural separation of infrastructure and services

The governance policy is versioned. Every change is logged in this file's git history.

---

*Governance Policy v1.0 · Kindling · Permanent Upper Class · March 2026*
