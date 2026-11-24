---
status: current
owner: MLAI engineering
last_verified: 2026-11-24
review_interval_days: 90
---

# Local development

## Workspace layout

Choose the checkout for your task using the [system map](SYSTEM_MAP.md#choosing-a-checkout).
In `platform`, run project commands inside `mlai-backend/`, `roo/` or
`mlai-chat/` and read that directory's instructions. For standalone work,
keep related repositories as siblings when their scripts require it. Some
backend content workflows expect a separately authorized `content-factory` checkout.

## Safe first checks

| Repository | Working directory | Install | Non-database check |
| --- | --- | --- | --- |
| `mlai-au` | repository root | `bun install --frozen-lockfile` | `bun run typecheck` |
| `mlai-backend` | repository root | Python 3.11 venv; install both requirements files | `python manage.py check` with a local SQLite URL |
| `roo` | `roo-standalone` | Python 3.11 venv; install `requirements.txt` | targeted import/static inspection; see repo README |

For Chat, select the client or relay in the project README and consult
`TESTING.md` for its checks.

Always prefer the current repository README and package scripts over this
summary.

## Migration approval gate

Never create, run, or apply a database migration without explicit approval for
the exact migration. Before running any setup, test, Compose, or deployment
command:

1. Inspect the command and the services it starts.
2. Determine whether it invokes a migration directly or indirectly.
3. Inspect the non-applying migration plan where the framework supports it.
4. Present the exact migration set and target database to the user.
5. Run it only after receiving explicit approval.

The backend's full local web container is one startup path that applies
migrations. Inspect Chat and Plane startup paths for the same side effect.

## Secrets

Example environment files describe names and safe shapes; they do not grant
access. Start with no secrets and add only the development or staging values
needed for the task. Never point a local checkout at production data by
convenience.

## Multi-repository work

Start the smallest useful set of services. A frontend-only task normally does
not require every worker. A contract change should use mocks or targeted local
services until an integration environment is genuinely necessary.

Before starting multiple services, write down:

- which service owns the contract;
- local ports and origins;
- which credentials are development-only;
- whether any process runs scheduled or background side effects; and
- whether any startup path invokes migrations.
