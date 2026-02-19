# .github

Organization-level GitHub defaults for [RentSpree](https://github.com/rentspree).

## Contents

| Path | Purpose |
|------|---------|
| `.github/ISSUE_TEMPLATE/*.yml` | Issue form templates (bug, feature, tech debt, operational) |
| `.github/ISSUE_TEMPLATE/config.yml` | Issue template chooser configuration |
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

`labels.yml` defines a shared label scheme using slash-prefixed categories:

| Prefix | Examples |
|--------|----------|
| `priority/` | critical, high, medium, low |
| `type/` | bug, feature, tech-debt, operational |
| `area/` | frontend, backend, infrastructure, data, integrations |
| `severity/` | critical, high, medium, low |
| `status/` | triage, accepted, in-progress, blocked, wont-fix |

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).
