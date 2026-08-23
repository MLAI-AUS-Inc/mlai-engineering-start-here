---
status: current
owner: MLAI engineering
last_verified: 2026-08-23
review_interval_days: 90
---

# Engineering workflow

## Before changing code or documentation

1. Identify the owning repository in `SYSTEM_MAP.md`.
2. Confirm the repository's actual default or task base branch; do not assume
   every repository uses `main`.
3. Read repository-local instructions.
4. Check for unrelated working-tree changes and preserve them.
5. Create a narrowly named branch from the agreed local base.

`mlai-plane` currently uses `preview` as its MLAI default branch. Upstream Plane
instructions referring to another default branch do not override that fact.

## Scope

Keep pull requests single-purpose. A documentation-only task changes
documentation files only: Markdown, documentation diagrams, and explicitly
approved machine-readable documentation inventories. It does not change CI,
scripts, application configuration, dependencies, migrations, or deployment
files.

## Validation

For documentation-only changes:

- inspect the final diff in every repository;
- verify relative links and referenced local paths;
- verify commands against current package files, task runners, or workflows;
- confirm no application or operational files changed; and
- do not start services solely for documentation validation.

For code changes, follow the owning repository's checks. Database-backed tests
or setup commands remain subject to the explicit migration approval gate.

## Pull requests

Each pull request should state:

- why the change belongs in that repository;
- whether behavior changed;
- what was validated;
- related pull requests in other repositories;
- rollout ordering if contracts span repositories; and
- any documentation that becomes authoritative or historical.

MLAI forks may contain upstream links and conventions. Confirm whether the
pull request belongs in `MLAI-AUS-Inc`, an upstream repository, or both.

## Cross-repository documentation changes

Use one branch name across repositories when practical. Do not combine Git
histories or create one commit spanning repositories. Each repository should
remain reviewable and mergeable independently; the central documentation
change should link the related pull requests when they exist.
