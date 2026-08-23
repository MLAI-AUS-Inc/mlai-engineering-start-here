---
status: current
owner: MLAI engineering
last_verified: 2026-08-23
review_interval_days: 90
---

# Runbook index

Operational details belong in the repository that owns the service. This page
routes maintainers to those documents without copying procedures.

## MLAI website

- Repository: [`mlai-au`](https://github.com/MLAI-AUS-Inc/mlai-au)
- Start with its README and `AGENTS.md`.
- Cloudflare configuration is repository-local; routine onboarding does not
  include deployment.

## MLAI backend

- Repository: [`mlai-backend`](https://github.com/MLAI-AUS-Inc/mlai-backend)
- Documentation index: `docs/README.md`
- MLAI Chat integration: `docs/mlai-chat-*.md`
- Organisational memory: `docs/org-memory-*.md`
- Reconciliation: `docs/*reconciliation*.md`

## Roo

- Repository: [`roo`](https://github.com/MLAI-AUS-Inc/roo)
- Active runtime root: `roo-standalone/`
- Service operations and incident notes: `roo-standalone/docs/`
- Runtime profiles: `roo-standalone/docker-compose*.yml`

## MLAI Chat

- Repository: [`mlai-chat`](https://github.com/MLAI-AUS-Inc/mlai-chat)
- Architecture: `ARCHITECTURE.md`
- Release guides: `RELEASING.md` and `docs/mlai/RELEASING.md`
- Hosted deployment: `deploy/mlai/README.md`
- Testing: `TESTING.md`

## MLAI Plane

- Repository: [`mlai-plane`](https://github.com/MLAI-AUS-Inc/mlai-plane)
- MLAI fork boundary: `MLAI.md`
- Upstream development instructions: `CONTRIBUTING.md`

## Plane edge gateway

- Repository: [`mlai-plane-edge`](https://github.com/MLAI-AUS-Inc/mlai-plane-edge)
- Security and local development: `README.md`
- Staging, cutover, rollback, and incidents: `RUNBOOK.md`
- Dated rehearsal evidence: `ACCEPTANCE.md`

## Migration safety

No runbook entry grants standing permission to create or apply a migration.
Every migration requires explicit approval for the exact migration and target,
including migrations invoked by setup, tests, Compose, or deployment tooling.
