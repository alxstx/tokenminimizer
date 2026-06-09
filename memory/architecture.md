# Architecture
<!-- Loaded ON DEMAND — the deep map an agent reads when it needs to navigate beyond AGENTS.md. Keep it factual, current, and skimmable (headers + bullets). Update it when structure changes, not on every edit. Delete sections that don't apply. -->

## System overview
<!-- One paragraph: what the system is, its main pieces, and how they fit — the mental model someone needs before reading any code. -->
{{overview}}

## Module map
<!-- dir/module → responsibility, deeper than AGENTS.md. Name the key file(s) per module so an agent can jump straight in. -->
- `{{path/}}` — {{responsibility}} (key files: `{{file}}`)
- `{{path/}}` — {{responsibility}} (key files: `{{file}}`)

## Data / control flow
<!-- How a request / job / command flows end to end. A short numbered sequence (or a small diagram) beats prose. -->
1. {{step}}
2. {{step}}

## Key abstractions
<!-- The 3–7 concepts you must understand to work here: the core types, the main interfaces, the central loop. -->
- **{{abstraction}}** — {{what it is, where it lives, why it matters}}

## State & storage
<!-- Databases, caches, queues, files, in-memory state. What's persisted where, and the source of truth for each kind of data. -->
{{state}}

## Cross-cutting concerns
<!-- How the codebase handles things that touch everything. Fill what applies; delete the rest. -->
- **Config / env:** {{how the app is configured}}
- **Auth / permissions:** {{model}}
- **Error handling:** {{pattern}}
- **Logging / observability:** {{approach}}
- **Validation:** {{approach}}

## Build, test & deploy
<!-- How the code becomes a running thing: CI stages, environments, release flow. -->
{{pipeline}}

## External dependencies & integrations
<!-- Services, APIs, queues, DBs, third-party SDKs the code relies on, and where each is used. -->
- {{dependency}} — {{how / where used}}

## Glossary (domain terms)
- **{{term}}** — {{meaning}}
