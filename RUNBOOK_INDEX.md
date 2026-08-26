---
status: current
owner: MLAI engineering
last_verified: 2026-08-24
review_interval_days: 90
---

# Runbook index

Operational details belong in the repository that owns the service. This page
routes maintainers to those documents without copying procedures.

If a service is not listed here, use [`SYSTEM_MAP.md`](SYSTEM_MAP.md) to
identify the owning repository first.

## MLAI website

- Repository: [`mlai-au`](https://github.com/MLAI-AUS-Inc/mlai-au)
- Start with its README and `AGENTS.md`.
- Cloudflare configuration is repository-local; routine onboarding does not
  include deployment.

## MLAI backend

- Repository: [`mlai-backend`](https://github.com/MLAI-AUS-Inc/mlai-backend)
- Documentation index: `docs/README.md`
- Historical Buzz/MLAI Chat experiment integration: `docs/mlai-chat-*.md`
- Organisational memory: `docs/org-memory-*.md`
- Reconciliation: `docs/*reconciliation*.md`

## Roo

- Repository: [`roo`](https://github.com/MLAI-AUS-Inc/roo)
- Active runtime root: `roo-standalone/`
- Service operations and incident notes: `roo-standalone/docs/`
- Runtime profiles: `roo-standalone/docker-compose*.yml`

## Inactive experiment references

The following documents are retained for investigation and historical context.
They are not current production runbooks and do not establish supported
services or operational readiness.

### Buzz / MLAI Chat experiment

- Repository: [`mlai-chat`](https://github.com/MLAI-AUS-Inc/mlai-chat)
- Architecture: `ARCHITECTURE.md`
- Release guides: `RELEASING.md` and `docs/mlai/RELEASING.md`
- Hosted deployment: `deploy/mlai/README.md`
- Testing: `TESTING.md`

### Plane experiment

- Repository: [`mlai-plane`](https://github.com/MLAI-AUS-Inc/mlai-plane)
- MLAI fork boundary: `MLAI.md`
- Upstream development instructions: `CONTRIBUTING.md`

### Plane edge experiment

- Repository: [`mlai-plane-edge`](https://github.com/MLAI-AUS-Inc/mlai-plane-edge)
- Security and local development: `README.md`
- Staging, cutover, rollback, and incidents: `RUNBOOK.md`
- Dated rehearsal evidence: `ACCEPTANCE.md`

## Migration safety

No runbook entry grants standing permission to create or apply a migration.
Every migration requires explicit approval for the exact migration and target,
including migrations invoked by setup, tests, Compose, or deployment tooling.
