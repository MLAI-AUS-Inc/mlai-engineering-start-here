---
status: current
owner: MLAI engineering
last_verified: 2026-08-23
review_interval_days: 90
---

# System map

## Product surfaces

```text
People and browsers
  |
  +-- mlai.au ----------------> mlai-au ---------> mlai-backend
  |
  +-- chat.mlai.au -----------> mlai-chat ------> mlai-backend integration APIs
  |
  +-- admin.mlai.au ----------> mlai-plane-edge -> private mlai-plane origin
  |
  +-- Slack ------------------> roo -------------> mlai-backend and approved integrations
```

The arrows show primary request relationships, not unrestricted trust. Each
service authenticates callers according to its own contract.

## Ownership matrix

| Capability | Owner | Important collaborators |
| --- | --- | --- |
| Public website and articles | `mlai-au` | `mlai-backend` for dynamic data |
| Browser authentication flows | `mlai-au` UI, `mlai-backend` contract/data | — |
| Founder Tools | `mlai-au` UI, `mlai-backend` API/data | External connectors |
| Hackathon browser apps | `mlai-au` | `mlai-backend` APIs, Roo for selected agent experiences |
| Shared users and organisations | `mlai-backend` | All authenticated product surfaces |
| Scheduled backend jobs | `mlai-backend` | Roo may call approved trigger APIs |
| Slack agent behavior | `roo` | `mlai-backend`, Linear, model providers |
| Community chat relay and clients | `mlai-chat` | `mlai-backend` identity/membership/bridge APIs |
| Plane application | `mlai-plane` | `mlai-plane-edge` |
| `admin.mlai.au` routing and cookie isolation | `mlai-plane-edge` | `mlai-plane`, Cloudflare |

## Repository boundaries

### `mlai-au`

Owns browser presentation and Cloudflare Worker behavior for `mlai.au`. It does
not own persistent backend data, scheduled work, chat, or Plane.

### `mlai-backend`

Owns shared Django APIs, identity, persistent data, integrations, and worker
processes. It must keep browser-origin and service-to-service trust explicit.

### `roo`

Owns Slack-facing AI routing and approved actions. Public and administrative
surfaces are separate security principals. Roo does not become the source of
truth for data owned by `mlai-backend` or Linear.

### `mlai-chat`

Owns the chat protocol, relay, clients, CLI, workflows, and agent harness. It is
an MLAI distribution fork of Buzz and retains upstream internal names.

### `mlai-plane`

Owns MLAI's Plane application fork. Product changes may be candidates for
upstream contribution, but MLAI deployment changes remain explicitly scoped.

### `mlai-plane-edge`

Owns the public edge boundary at `admin.mlai.au`. It strips MLAI parent-domain
credentials before requests reach Plane and keeps Plane origin credentials out
of the browser.

## When more than one repository changes

A cross-repository change should name:

- the repository that owns the contract;
- every consumer of the contract;
- rollout order;
- compatibility window;
- rollback owner; and
- documentation that becomes authoritative after rollout.

Do not duplicate one repository's detailed API schema or runbook here. Link to
the owning repository and record only the cross-repository dependency.
