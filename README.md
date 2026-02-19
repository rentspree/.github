# .github

Organization-level GitHub defaults for [RentSpree](https://github.com/rentspree).

## Contents

| Path | Purpose |
|------|---------|
| `.github/ISSUE_TEMPLATE/*.yml` | Issue form templates (bug, feature, tech debt, operational) |
| `.github/ISSUE_TEMPLATE/config.yml` | Issue template chooser configuration |
| `.github/workflows/sync-labels.yml` | Label sync workflow |
| `labels.yml` | Canonical label taxonomy for all repositories |
| `CODEOWNERS` | Default code ownership |
| `CONTRIBUTING.md` | Contributing guidelines |

## How It Works

Files in this repository serve as [community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) defaults. Any RentSpree repository that does not define its own versions will inherit these files automatically.

Repositories can override any default by placing their own version in their `.github/` directory.

## Issue Templates

Four issue form templates are available org-wide:

- **Bug Report** — Repro steps, expected/actual behavior, environment
- **Feature Request** — Problem statement, proposed solution, acceptance criteria
- **Tech Debt** — Current state, desired state, affected file paths
- **Operational Issue** — Severity, impact, mitigation steps

## Label Taxonomy

`labels.yml` defines a shared label scheme using a hybrid naming convention:

- **Prefixed** (`key/value`) for multi-value categories where grouping aids filtering
- **Simple** names for standalone type and AI labels (reuses GitHub defaults)

| Category | Style | Examples |
|----------|-------|----------|
| Type | simple | `bug`, `enhancement`, `tech-debt`, `operational` |
| `priority/` | prefixed | critical, high, medium, low |
| `area/` | prefixed | frontend, backend, infrastructure, data, integrations |
| `severity/` | prefixed | critical, high, medium, low |
| `status/` | prefixed | triage, accepted, in-progress, blocked, wont-fix |
| `bot/` | prefixed | md-drift, summary, md-first-gen |
| AI | simple | `ai-candidate`, `ai-assigned`, `claude-code-assisted` |
| Team | simple | `team-ada`, `team-infradevex`, `team-magenta`, etc. |

### Label Sync

Labels are synced to all non-archived repos via the `sync-labels.yml` workflow. The sync is **additive** — it creates or updates labels from `labels.yml` but does **not** delete repo-local labels (e.g., release/semver labels used by library repos).

The sync runs automatically when `labels.yml` changes, or can be triggered manually.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).
