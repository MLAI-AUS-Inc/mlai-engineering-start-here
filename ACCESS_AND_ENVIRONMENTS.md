---
status: current
owner: MLAI engineering
last_verified: 2026-08-23
review_interval_days: 90
---

# Access and environments

## Least-access onboarding

A new engineer should begin with:

- access to the required MLAI GitHub repositories;
- local toolchains for the assigned repository; and
- example environment files containing no live secrets.

Production SSH, production databases, broad cloud credentials, and unrelated
integration tokens are not onboarding requirements.

## Environment intent

| Environment | Purpose | Data and credentials |
| --- | --- | --- |
| Local | Development and narrow validation | Synthetic/local data; no production secrets |
| CI | Repeatable automated validation | Repository-scoped ephemeral credentials |
| Staging or development integration | Approved external integration testing | Explicitly provisioned non-production credentials |
| Production | User-facing service | Restricted operational access and reviewed workflows |

The exact environment names and deployment mechanisms are owned by each
repository. Do not infer that a similarly named variable has the same authority
across services.

## Requesting access

Ask for access only after identifying:

1. the feature being tested;
2. the service and environment;
3. the minimum required scope;
4. the expected duration; and
5. whether a local mock or staging credential is sufficient.

Do not put secret values or password-manager retrieval details into committed
documentation. Documentation may name the responsible team or approval path.

## High-risk access

The following require explicit task-specific authorization:

- production database or SSH access;
- deployment, Cloudflare, or container-host administration;
- Slack or Linear credentials capable of writes;
- administrative Roo credentials;
- credentials able to alter authentication, billing, or user data; and
- any action that creates, runs, or applies a database migration.

Possessing a credential does not authorize its use for an unrelated task.
