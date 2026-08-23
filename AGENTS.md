---
status: current
owner: MLAI engineering
last_verified: 2026-08-24
review_interval_days: 90
---

# Cross-repository AI agent guide

This repository contains documentation only. Do not add application code,
credentials, deployment automation, or environment-specific secret values.

## Required reading order

Before changing another repository:

1. Read [`SYSTEM_MAP.md`](SYSTEM_MAP.md) and identify the owner of the behavior.
2. Read the target repository's `AGENTS.md` completely.
3. Read its README and the task-specific architecture or runbook.
4. Inspect current code and configuration before trusting a dated plan.
5. Keep the change inside the repository that owns it unless the task explicitly
   requires coordinated changes.

## Hard constraints

- Never create, run, or apply a database migration without explicit approval
  for that specific migration.
- Treat setup scripts, tests, Compose startup, and deployment tools that apply
  migrations indirectly as migration commands.
- Never deploy, cut over traffic, rotate credentials, send messages, modify
  external records, or run operational repair actions unless explicitly asked.
- Never put secrets, credential locations containing secret values, private
  customer data, or copied production configuration in documentation.
- Do not infer that a plan, audit, acceptance record, or incident report
  describes current production state.

## Documentation changes

When changing architecture or onboarding documentation:

- Use exact repository names, file paths, commands, ports, and ownership terms.
- Say what a component does not own when the boundary could be confused.
- Link to service-owned details instead of copying them here.
- Separate current instructions from proposals and historical context.
- Update `machine/repositories.yaml` when repository ownership changes.
- Preserve front matter and advance `last_verified` only after checking the
  document against current repository state.

For documentation-only work, validate Markdown links, referenced paths, and Git
diffs. Do not start services or run database-backed test suites merely to prove
a documentation edit.

## Routing changes between repositories

| Concern | Owning repository |
| --- | --- |
| `mlai.au` browser UI | `mlai-au` |
| Shared API, identity, or persistent MLAI product data | `mlai-backend` |
| Slack-facing agent behavior | `roo` |
| Buzz deployment experiment | `mlai-chat` (inactive; explicit task required) |
| Plane deployment experiment | `mlai-plane` and `mlai-plane-edge` (inactive; explicit task required) |

If ownership is unclear, document the ambiguity rather than introducing a new
cross-service dependency by assumption.
