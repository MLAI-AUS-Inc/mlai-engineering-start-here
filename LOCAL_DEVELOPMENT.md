---
status: current
owner: MLAI engineering
last_verified: 2026-08-24
review_interval_days: 90
---

# Local development

## Workspace layout

Keep active repositories as siblings so cross-repository scripts can resolve
their expected paths:

```text
MLAI/
├── mlai-engineering/
├── mlai-au/
├── mlai-backend/
└── roo/
```

Clone only the repositories needed for the task. Some backend content workflows
also expect a separately authorized sibling `content-factory` repository.

## Safe first checks

| Repository | Working directory | Install | Non-database check |
| --- | --- | --- | --- |
| `mlai-au` | repository root | `bun install --frozen-lockfile` | `bun run typecheck` |
| `mlai-backend` | repository root | Python 3.11 venv; install both requirements files | `python manage.py check` with a local SQLite URL |
| `roo` | `roo-standalone` | Python 3.11 venv; install `requirements.txt` | targeted import/static inspection; see repo README |

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

The active known example that crosses this gate is `mlai-backend`'s full local
web container. The inactive Buzz and Plane experiments also contain setup paths
that apply migrations; do not run them unless an explicit task reactivates the
experiment and approves the exact migration set.

## Inactive experiments

`mlai-chat`, `mlai-plane`, and `mlai-plane-edge` are not part of the standard
workspace or onboarding path. Clone or run them only for an explicitly scoped
historical investigation or reactivation decision. Repository-local commands
describe the experiment, not a supported MLAI development environment.

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
