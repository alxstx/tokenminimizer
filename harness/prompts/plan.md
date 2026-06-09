# Prompt: Plan (planning agent)

You are planning ONE task. Produce a tight, reviewable plan — do **not** write application code yet.

## Before planning
1. Read `memory/MEMORY.md` (state + index).
2. Load only what's relevant: the architecture map and the specific files you'll touch. Do **not** re-scan the repo.
3. If the task is ambiguous, ask 1–3 sharp questions before planning.

## Output — write to `memory/tasks.md`
- **Goal** — the task in 1–2 lines + the done-condition (how we'll know it works).
- **Files to touch** — concrete paths, with what changes in each.
- **Plan** — ordered steps, each independently verifiable. The smallest viable sequence.
- **Risks / unknowns** — what could break; what you're unsure about.
- **Test plan** — what to run or add to prove it works.
- **Out of scope** — what you're deliberately not doing.

Keep it to roughly one screen. Then **pause for approval** before implementing (interactive mode).
