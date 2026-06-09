# token-harness

A **token-minimizing, tool-agnostic markdown harness** for doing implementation work with AI coding agents (GitHub Copilot, Cursor, Claude Code, Codex…).

It keeps a tiny always-loaded brief plus a live memory index in context and pushes everything else to files loaded on demand — so an agent can work in your repo without re-reading the whole thing every session.

**Core rule: index in context, detail on disk.** Only `AGENTS.md` and `memory/MEMORY.md` load by default (a few hundred tokens). Everything else is pulled in just-in-time.

## How it works
```
always loaded, every session ─────▶  AGENTS.md  +  memory/MEMORY.md           (~1–2K tokens)
loaded only when the task needs ──▶  memory/{architecture,decisions,tasks}.md · source files
invoked on demand (not always-on) ▶  /bootstrap-fill /bootstrap-verify /plan /implement /verify-change
```

## Quickstart
1. Copy `AGENTS.md`, `memory/`, `harness/`, and `.github/` into your repo.
2. Run `/bootstrap-fill` (Copilot) or paste `harness/prompts/1-bootstrap-fill.md` — an agent fills `AGENTS.md` and seeds `memory/` from your repo.
3. Run `/bootstrap-verify` — a second agent checks it against the real repo and flags/fixes errors.
4. Skim the report; fix anything flagged. (~5 min)
5. Per task: `/plan` → approve → `/implement` → `/verify-change`.

## What's inside
| Path | Loaded | Purpose |
|---|---|---|
| `AGENTS.md` | always | Project brief + operating contract (the template). < 200 lines. |
| `memory/MEMORY.md` | always | Live state + index. < 60 lines. |
| `memory/{architecture,decisions,tasks}.md` | on demand | Map / why-log / active plan. |
| `.github/prompts/*.prompt.md` | invoked | Copilot slash commands: `/plan`, `/implement`, `/verify-change`, `/bootstrap-fill`, `/bootstrap-verify`. |
| `.github/instructions/*.instructions.md` | path-scoped | Rules that load only for files matching `applyTo`. |
| `.github/copilot-instructions.md` | always (Copilot) | Forces "read memory first" behavior. |
| `harness/` | reference | Canonical prompts, templates, and full docs ([`harness/README.md`](harness/README.md)). |

## Principles
- **Progressive disclosure** — an index in context, detail on disk; on-demand files cost nothing until opened.
- **Externalized memory** — durable facts live in `memory/` and are read back later, not held in a context window that resets each session.
- **Invocation over always-on** — the "agents" are prompts you fire, not definitions loaded on every message.

Full design notes, token math, customization, and FAQ: [`harness/README.md`](harness/README.md).

## Why so few agents
Existing agent frameworks tend to add agents — and tokens; some ship hundreds of thousands of tokens of always-on agent definitions, and multi-agent setups routinely burn 4–15× the tokens. This harness does the opposite: **prompts you invoke** instead of always-on agents, and only three roles that pay for themselves — **onboard, plan, verify** — plus the main loop. The token win is *progressive disclosure* + *invocation isolation*, not more agents.

---
A starting point — fork it, tune the prompts, make it yours.
