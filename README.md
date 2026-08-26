---
status: current
owner: MLAI engineering
last_verified: 2026-08-24
review_interval_days: 90
---

# MLAI engineering: start here

This repository is the entry point for engineers and AI coding agents working
across MLAI's software repositories. It explains which repository owns each
part of the platform, how services relate, and where authoritative development
and operational instructions live.

It does not contain application code, production credentials, or copies of
service-specific runbooks.

## First hour

1. Read [`SYSTEM_MAP.md`](SYSTEM_MAP.md) to identify the owning repository.
2. Read [`ARCHITECTURE.md`](ARCHITECTURE.md) for service relationships and
   trust boundaries.
3. Clone only the repositories needed for the task.
4. Read the target repository's `README.md` and `AGENTS.md` completely.
5. Follow [`ACCESS_AND_ENVIRONMENTS.md`](ACCESS_AND_ENVIRONMENTS.md) before
   requesting credentials.
6. Use [`LOCAL_DEVELOPMENT.md`](LOCAL_DEVELOPMENT.md) for safe setup paths.
7. Follow [`ENGINEERING_WORKFLOW.md`](ENGINEERING_WORKFLOW.md) for branches,
   validation, and pull requests.

## Active repositories

| Repository | Primary responsibility | Runtime |
| --- | --- | --- |
| [`mlai-au`](https://github.com/MLAI-AUS-Inc/mlai-au) | Public website and browser applications | React Router on Cloudflare Workers |
| [`mlai-backend`](https://github.com/MLAI-AUS-Inc/mlai-backend) | Django APIs, identity, persistent data, integrations, jobs, and workers | Python/Django containers |
| [`roo`](https://github.com/MLAI-AUS-Inc/roo) | Slack-facing public and administrative AI agent services | Python/FastAPI containers |

## Inactive open-source deployment experiments

These repositories are retained as experiment history. They are not active,
supported MLAI platform components and should not be cloned during normal
onboarding or represented as current production architecture.

| Repository | Experiment |
| --- | --- |
| [`mlai-chat`](https://github.com/MLAI-AUS-Inc/mlai-chat) | Deploying and adapting the open-source Buzz collaboration platform |
| [`mlai-plane`](https://github.com/MLAI-AUS-Inc/mlai-plane) | Deploying and adapting the open-source Plane project-management platform |
| [`mlai-plane-edge`](https://github.com/MLAI-AUS-Inc/mlai-plane-edge) | Edge-routing prototype created for the Plane deployment experiment |

Work in an experimental repository only when a task explicitly reactivates or
investigates that experiment. Its README may describe intended deployment
behavior that was never adopted as current MLAI architecture.

See [`machine/repositories.yaml`](machine/repositories.yaml) for a compact,
machine-readable version of this inventory.

## Non-negotiable safety rule

> Never create, run, or apply a database migration without explicit approval
> for that specific migration.

This includes migrations invoked indirectly by setup scripts, tests, container
startup, or deployment commands. Inspecting a migration plan does not grant
permission to apply it.

## Documentation authority

Use this order when documents overlap:

1. Explicit instructions from the user for the current task
2. The target repository's `AGENTS.md`
3. The target repository's current README, architecture, and runbook
4. This cross-repository guide
5. Dated audits, implementation plans, and archived material

The repository that owns a service also owns its detailed setup, configuration,
API contract, deployment, and incident documentation. This central repository
owns only cross-repository architecture and onboarding.

## Documentation map

- [`SYSTEM_MAP.md`](SYSTEM_MAP.md): repository and product ownership
- [`ARCHITECTURE.md`](ARCHITECTURE.md): end-to-end request paths and trust boundaries
- [`LOCAL_DEVELOPMENT.md`](LOCAL_DEVELOPMENT.md): safe setup and multi-repo workflows
- [`ENGINEERING_WORKFLOW.md`](ENGINEERING_WORKFLOW.md): contribution lifecycle
- [`ACCESS_AND_ENVIRONMENTS.md`](ACCESS_AND_ENVIRONMENTS.md): access and credential model
- [`RUNBOOK_INDEX.md`](RUNBOOK_INDEX.md): links to service-owned operations guides
- [`AGENTS.md`](AGENTS.md): instructions for AI coding agents
- [`machine/repositories.yaml`](machine/repositories.yaml): machine-readable repository inventory

## Keeping this current

Update this repository when a repository is created, renamed, archived, changes
ownership, gains a production surface, or changes a trust boundary. Update the
owning repository when implementation details or commands change.

`last_verified` means the document was checked against current repositories; it
is not merely the date of the last wording change.
