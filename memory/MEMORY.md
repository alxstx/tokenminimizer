# Memory — live index
<!-- The ONLY memory file loaded by default. Keep it SHORT (aim < 60 lines). Detail lives in topic files — link, don't inline. Prune ruthlessly. -->

## Current focus
{{What we're doing right now — 1–3 lines. After bootstrap: "Freshly onboarded; no active task."}}

## Recent changes (newest first — keep ~7 max)
- {{date}} — {{change, with path:line if useful}}

## Open questions / TODO
- {{item}}

## Gotchas (surprising facts that bit us — keep ~7 max)
- {{gotcha}}

## Index (load on demand)
- `architecture.md` — module map, data/control flow, key abstractions, glossary
- `decisions.md` — why we did things (ADR-lite)
- `tasks.md` — active plan & progress for the current task

## Update rules
- After a meaningful change: add one line to **Recent changes**; move anything durable into the right topic file.
- When **Current focus** changes: rewrite it; archive the finished plan out of `tasks.md`.
- If this file passes ~60 lines, prune the oldest Recent changes / Gotchas. The index stays; the log rotates.
