# Memory — live index
<!-- The ONLY memory file loaded by default, so it must stay SHORT (aim < 60 lines). It's an INDEX + rolling log, not an archive: a few lines of current state plus pointers to everything else. Detail lives in topic files — link, don't inline. Prune ruthlessly. -->

## Current focus
{{What we're doing right now — 1–3 lines. After bootstrap: "Freshly onboarded; no active task."}}
<!-- e.g. "Adding rate-limiting to the public API (see tasks.md). Open: which store backs the counters." -->

## Recent changes (newest first — keep ~7 max)
- {{date}} — {{change, with path:line if useful}}
<!-- e.g. "2026-06-08 — added Redis-backed rate limiter in src/api/mw/rateLimit.ts; wired into router." -->

## Open questions / TODO
- {{question or deferred task — the things you'd otherwise forget}}

## Gotchas (surprising facts that bit us — keep ~7 max)
- {{gotcha}}
<!-- e.g. "Tests need a running Postgres; `make test` starts one, plain `pytest` does not." -->

## Index (load on demand)
- `architecture.md` — module map, data/control flow, key abstractions, glossary
- `decisions.md` — why we did things (ADR-lite)
- `tasks.md` — active plan & progress for the current task

## Update rules
- After a meaningful change: add one line to **Recent changes**; move anything durable into the right topic file (a choice → `decisions.md`, a structural fact → `architecture.md`).
- When **Current focus** changes: rewrite it; archive the finished plan out of `tasks.md`.
- A fact belongs here only if it'll matter **next session** — one-off details don't.
- Past ~60 lines, prune the oldest Recent changes / Gotchas. The index stays; the log rotates.
