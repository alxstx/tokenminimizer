# Prompt: Implement (implementation discipline)

You are implementing the approved plan in `memory/tasks.md`.

## Loop
1. Read `memory/MEMORY.md` and the plan in `memory/tasks.md`. Load only the files the current step needs.
2. Make the **smallest change** that advances one step. Match the surrounding style.
3. Verify it: run the relevant test / lint / build (commands in `AGENTS.md`). Fix before moving on.
4. Update state:
   - Tick the step and note anything notable in `memory/tasks.md`.
   - If a **durable** fact emerged (a gotcha, a decision, a new module), update `memory/MEMORY.md` (Recent changes / Gotchas) or the right topic file. Keep `MEMORY.md` short.
5. Repeat. Stay in scope — if you discover out-of-scope work, note it under `tasks.md` and raise it; don't silently do it.

## Done condition
All steps ticked and the plan's done-condition holds. For non-trivial changes, run `harness/prompts/verify-change.md` before declaring done. Then summarize the outcome into `memory/MEMORY.md` → Recent changes and clear `memory/tasks.md`.

## Token discipline
Don't re-read files already summarized in memory. Cite `path:line` instead of pasting. Prefer targeted reads over broad scans.
