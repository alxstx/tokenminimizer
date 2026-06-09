<!-- token-harness v0.1 | pristine template — copy to repo root as AGENTS.md, then run harness/prompts/1-bootstrap-fill.md -->
# {{PROJECT_NAME}}

> {{ONE_LINE_PURPOSE}}

## How to work here (operating contract)
- **Read `memory/MEMORY.md` first** every task — it's the live state + index. Do **not** re-scan the whole repo; use the map below and the memory index.
- Load detail **on demand**: architecture → `memory/architecture.md`; the "why" behind choices → `memory/decisions.md`; the current plan → `memory/tasks.md`.
- Keep changes **small and verifiable**. Stay within the task's scope; surface scope creep instead of doing it silently.
- After any meaningful change, **update memory** (rules are in `memory/MEMORY.md`). Keep the index short; push detail to topic files.
- This repo runs **interactive**: propose a plan and pause for approval before large or irreversible changes.
- Verify before declaring done: run the checks below, and for non-trivial changes run `harness/prompts/verify-change.md`.

## Stack & commands
<!-- fill: copy real commands from package scripts / Makefile / justfile / CI. Be exact. -->
- **Languages / frameworks:** {{STACK}}
- **Install:** `{{INSTALL_CMD}}`
- **Build:** `{{BUILD_CMD}}`
- **Test:** `{{TEST_CMD}}`  (single test: `{{TEST_ONE_CMD}}`)
- **Lint / format:** `{{LINT_CMD}}` / `{{FORMAT_CMD}}`
- **Run locally:** `{{RUN_CMD}}`

## Architecture map (where things live)
<!-- fill: one line per top-level dir/module that matters — path → responsibility. This is what lets an agent navigate without re-reading the repo. Deeper detail goes in memory/architecture.md. -->
- `{{path/}}` — {{responsibility}}
- `{{path/}}` — {{responsibility}}

Entry point(s): {{ENTRYPOINTS}}. Request/data flow: {{ONE_LINE_DATA_FLOW}}.

## Conventions
<!-- fill: only non-obvious, enforceable rules. Concrete > abstract. Add a tiny do/don't only where it prevents a repeated mistake. -->
- {{CONVENTION}}
- {{CONVENTION}}

## Boundaries (do not touch without asking)
- {{GENERATED_OR_VENDORED_PATHS}}, {{SECURITY_SENSITIVE_AREAS}}, {{MIGRATIONS}}

## Pointers
- Glossary / domain terms: `memory/architecture.md`
- External docs / dashboards / tickets: {{LINKS}}
