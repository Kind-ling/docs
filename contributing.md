# Contributing to Kindling

Kindling is open-source infrastructure. Contributions are welcome across all modules.

---

## Ways to Contribute

### Code
- Bug fixes — open an issue first, then a PR
- New adapters (Igniter middleware for Fastify, Hono, Django, etc.)
- Verifier improvements (new anti-sybil measures, scoring refinements)
- Documentation improvements

### Benchmark Submissions
Community benchmark submissions are the foundation of Kindling Documenter's credibility.

**Requirements for a valid community benchmark:**
1. Methodology documented before results (not after)
2. At minimum 3 independent runs
3. Competitor services included
4. Raw data published alongside results
5. No financial relationship with the benchmarked service undisclosed

Submit via GitHub issue with label `benchmark-submission`.

### Methodology Challenges
If you believe a Verifier score is computed incorrectly:

1. Open a GitHub issue with label `score-challenge`
2. Include: the specific score disputed, the methodology section in question, and supporting data
3. We respond within 72 hours with acknowledgment
4. Resolution within 14 days
5. Score annotated "under review" during the process
6. Resolution published publicly regardless of outcome

### Governance Feedback
Governance policy changes are open for public comment. Watch this repo for proposed changes.

---

## Development Setup

```bash
# Twig
git clone https://github.com/Kind-ling/twig
cd twig && npm install && npm test
# npx @kind-ling/twig analyze <url>

# Heat
git clone https://github.com/Kind-ling/heat
cd heat && npm install && npm test
# npm start — starts on :3000

# Igniter
git clone https://github.com/Kind-ling/igniter
cd igniter && npm install && npm test
# npx @kind-ling/igniter init

# Python (Igniter FastAPI adapter)
cd packages/fastapi
pip install -e ".[dev]"
pytest
```

---

## Pull Request Guidelines

- Small, focused PRs are preferred over large ones
- Tests required for new functionality
- TypeScript: strict mode, no `any`
- Python: type hints, no untyped functions
- Docs updated alongside code changes
- New defaults documented in `kindling.config.yml`

---

## Code of Conduct

Be direct. Be honest. Assume good faith. Don't be cruel.

Contributions that introduce hidden affiliate behavior, manipulate scoring, or undermine the governance policy will be rejected.

---

## First-Party Disclosure for Contributors

If you are affiliated with a service indexed by Kindling Verifier, disclose it when contributing to scoring or benchmark code. This is not disqualifying — it's just required.

---

*Contributing v1.0 · Kindling · March 2026*
