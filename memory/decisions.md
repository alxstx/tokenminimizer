# Decisions (ADR-lite)
<!-- Loaded ON DEMAND. The "why" memory, so settled choices aren't re-litigated and an agent doesn't "fix" something deliberate. Append newest-last; don't rewrite history — mark a reversed decision as superseded. -->

Add an entry when you: pick between real alternatives, adopt or drop a dependency, set a convention with trade-offs, or make a choice a future reader would question. Skip the obvious.

<!-- TEMPLATE — copy per decision:

## {{date}} — {{title}}
- **Decision:** {{what was decided}}
- **Why:** {{the constraint that forced it}}
- **Alternatives considered:** {{what else, and why not}}
- **Status:** accepted | superseded by {{date / title}}

EXAMPLE (delete on first real use):

## 2026-06-08 — Redis for rate-limit counters
- **Decision:** Store rate-limit counters in Redis, not Postgres.
- **Why:** Counters are hot, short-lived, and per-request; Postgres writes were the bottleneck under spikes.
- **Alternatives considered:** Postgres (write amplification); in-process memory (breaks across multiple app instances).
- **Status:** accepted
-->
