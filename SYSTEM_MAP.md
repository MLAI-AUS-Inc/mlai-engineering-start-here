---
status: current
owner: MLAI engineering
last_verified: 2026-08-24
review_interval_days: 90
---

# System map

## Active product surfaces

```text
People and browsers
  |
  +-- mlai.au ----------------> mlai-au ---------> mlai-backend
  |
  +-- Slack ------------------> roo -------------> mlai-backend and approved integrations
```

The arrows show primary request relationships, not unrestricted trust. Each
service authenticates callers according to its own contract.

## Active ownership matrix

| Capability | Owner | Important collaborators |
| --- | --- | --- |
| Public website and articles | `mlai-au` | `mlai-backend` for dynamic data |
| Browser authentication flows | `mlai-au` UI, `mlai-backend` contract/data | — |
| Founder Tools | `mlai-au` UI, `mlai-backend` API/data | External connectors |
| Hackathon browser apps | `mlai-au` | `mlai-backend` APIs, Roo for selected agent experiences |
| Shared users and organisations | `mlai-backend` | Authenticated product surfaces |
| Scheduled backend jobs | `mlai-backend` | Roo may call approved trigger APIs |
| Slack agent behavior | `roo` | `mlai-backend`, Linear, model providers |

## Active repository boundaries

### `mlai-au`

Owns browser presentation and Cloudflare Worker behavior for `mlai.au`. It does
not own persistent backend data or scheduled work.

### `mlai-backend`

Owns shared Django APIs, identity, persistent data, integrations, and worker
processes. It must keep browser-origin and service-to-service trust explicit.

### `roo`

Owns Slack-facing AI routing and approved actions. Public and administrative
surfaces are separate security principals. Roo does not become the source of
truth for data owned by `mlai-backend` or Linear.

## Inactive open-source deployment experiments

These repositories are retained for experiment history and possible future
evaluation. They are not supported product surfaces or current architecture:

- `mlai-chat`: experiment deploying and adapting the open-source Buzz
  collaboration platform;
- `mlai-plane`: experiment deploying and adapting the open-source Plane
  project-management platform; and
- `mlai-plane-edge`: Cloudflare edge-routing prototype created for the Plane
  experiment.

Documentation inside these repositories describes their intended experimental
design. It must not be used as evidence that `chat.mlai.au`, `admin.mlai.au`, or
their associated services are active.

## When more than one active repository changes

A cross-repository change should name:

- the repository that owns the contract;
- every consumer of the contract;
- rollout order;
- compatibility window;
- rollback owner; and
- documentation that becomes authoritative after rollout.

Do not duplicate one repository's detailed API schema or runbook here. Link to
the owning repository and record only the cross-repository dependency.
