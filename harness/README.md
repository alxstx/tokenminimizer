# Token-minimizing harness (tool-agnostic)

A thin set of markdown files that lets any coding agent (Copilot, Cursor, Claude Code, Codex…) do implementation work **without re-reading your whole repo every session**. It keeps a tiny always-loaded brief plus a live memory index in context, and pushes everything else to files loaded on demand.

**Core rule: index in context, detail on disk.** The only files an agent loads by default are `AGENTS.md` and `memory/MEMORY.md` (a few hundred tokens). Everything else is pulled in just-in-time.

## The flow — one-time bootstrap, then repeatable use
1. **Drop** the harness into a repo: copy `AGENTS.md`, `memory/`, `harness/`, and — for Copilot — `.github/`.
2. **Fill** — paste `harness/prompts/1-bootstrap-fill.md` to an agent. It reads the repo and fills `AGENTS.md` + seeds `memory/`.
3. **Verify** — paste `harness/prompts/2-bootstrap-verify.md`. A second agent checks the filled harness against the real repo and flags/fixes errors.
4. **Hand-verify** — skim the report; fix anything marked `(?)`, `✗`, or `⚠`. ~5 minutes.
5. **Use** — per task: `plan.md` → *(you approve)* → `implement.md` → `verify-change.md`. Memory updates as you go.

## File map
| File | Loaded | Purpose |
|---|---|---|
| `AGENTS.md` | **always** | Project brief + operating contract. The filled template. < 200 lines. |
| `memory/MEMORY.md` | **always** | Live state + index: current focus, recent changes, gotchas, pointers. < 60 lines. |
| `memory/architecture.md` | on demand | Module map, data flow, key abstractions, glossary. |
| `memory/decisions.md` | on demand | Why-log (ADR-lite). |
| `memory/tasks.md` | on demand | Active plan & progress. Survives context resets. |
| `harness/prompts/*.md` | invoked | Canonical prompts: fill, verify, plan, implement, verify-change. |
| `.github/prompts/*.prompt.md` | invoked | Copilot slash commands (`/plan`, `/implement`, …) that call the canonical prompts. |
| `.github/instructions/*.instructions.md` | path-scoped | Rules that load only for files matching `applyTo`. |
| `harness/templates/*` | reference | Pristine `AGENTS.template.md` for re-bootstrapping. |

## Why so few agents?
Multi-agent frameworks routinely ship 20–100+ always-on agent files — one popular one shipped ~300K tokens of agent definitions loaded on *every* message, most non-functional. Multi-agent setups also burn 4–15× the tokens. This harness uses **prompts you invoke**, not always-on agents, and only the roles that pay for themselves: **onboard, plan, verify**. The implementation work is just you + the brief. The token win comes from *isolation* (run the expensive read/verify in a separate invocation that returns a short result) and *progressive disclosure* (load detail only when needed), not from more agents.

## Wiring it into your tool
- **GitHub Copilot** — `AGENTS.md` is read natively, and `.github/copilot-instructions.md` forces memory-first behavior. Slash commands ship in `.github/prompts/` — `/plan`, `/implement`, `/verify-change`, `/bootstrap-fill`, `/bootstrap-verify` (thin wrappers that call the canonical `harness/prompts/*.md`). For narrow rules that cost no tokens elsewhere, see `.github/instructions/example.instructions.md` (`applyTo:` globs).
- **Cursor** — add a `.cursor/rules/*.mdc` (or `.cursorrules`) that says "read `AGENTS.md` and `memory/MEMORY.md` first."
- **Claude Code** — add a `CLAUDE.md` containing `@AGENTS.md`; its native auto-memory can supplement `memory/`.
- **Any tool** — plain markdown: paste the prompt, attach `AGENTS.md` + `memory/MEMORY.md` as context.

## Keeping it cheap (token hygiene)
- Keep `AGENTS.md` < 200 lines and `memory/MEMORY.md` < 60. If they grow, move detail to topic files.
- Update memory in small increments during work; prune the index — it's a rotating log, not an archive.
- Cite `path:line`; don't paste big code into memory.
- Anything that "must happen every time" (run tests, lint) belongs in CI or a tool hook, not in prose the model has to remember.

## Tag
The harness is marked `token-harness v0.1` at the top of `AGENTS.md` and `harness/templates/AGENTS.template.md`, so you can tell a repo is harnessed and which version it's on. Bump it when you change the template.
