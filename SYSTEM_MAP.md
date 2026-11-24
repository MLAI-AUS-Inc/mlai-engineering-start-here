---
status: current
owner: MLAI engineering
last_verified: 2026-11-24
review_interval_days: 90
---

# System map

## Active product surfaces

```text
People and browsers
  |
  +-- mlai.au ----------------> mlai-au ---------> mlai-backend
  |
  +-- Member clients --------> mlai-chat relay and mlai-backend APIs
  |
  +-- Slack ------------------> roo -------------> mlai-backend and approved integrations
```

The arrows show primary request relationships, not unrestricted trust. Each
service authenticates callers according to its own contract.

## Active ownership matrix

| Capability | Owner | Important collaborators |
| --- | --- | --- |
| Public website and article rendering | `mlai-au` | `mlai-backend` for dynamic data |
| Article drafting and publishing | `mlai-chat` | GitHub connection publishes content to `mlai-au` |
| Project and event channels | `mlai-backend` synchronizes managed channels | `mlai-chat` groups and displays channels |
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

### `mlai-chat`

Owns the member workspace, clients and conversation relay. The backend owns
shared MLAI identity and domain records used by the clients.

## Choosing a checkout

- Website changes belong in `mlai-au`.
- For backend and Roo staging deployment changes, use the
  [workflow in platform](https://github.com/MLAI-AUS-Inc/platform/blob/main/.github/workflows/deploy.yml).
- For backend, Roo and Chat feature work, the standalone repositories continue
  to merge PRs. The [platform guide](https://github.com/MLAI-AUS-Inc/platform/blob/main/AGENTS.md)
  also supports coordinated changes in its `mlai-backend/`, `roo/` and
  `mlai-chat/` directories. Follow the destination named in the issue or
  existing PR. If it is unspecified, confirm the target with the maintainer
  before branching.

## Plane staging

`mlai-plane` owns the application fork. `mlai-plane-edge` owns the Cloudflare
gateway and documents the canonical staging domain. See the
[operations index](RUNBOOK_INDEX.md#plane-staging) for staging and cutover guidance.

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
