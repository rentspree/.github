# Copilot Instructions

This file provides guidance to GitHub Copilot when working with code in this repository.

## Repository Overview

This is a **configuration-only repository** (no build, lint, or test commands). It provides **organization-level GitHub defaults** for all RentSpree repositories:

- **Issue form templates** (`.github/ISSUE_TEMPLATE/`) -- YAML-based forms for bug reports, feature requests, tech debt, and operational issues
- **Label taxonomy** (`labels.yml`) -- canonical labels synced across all RentSpree repos
- **Contributing guidelines** (`CONTRIBUTING.md`) and **code ownership** (`CODEOWNERS`)

## Issue Templates

Templates use [GitHub Issue Forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues/syntax-for-issue-forms) YAML syntax (not legacy Markdown templates).

### Structure

Each `.yml` template has:
- Top-level: `name`, `description`, `labels` (auto-applied)
- `body`: array of form elements (`markdown`, `input`, `textarea`, `dropdown`)
- Each element has: `type`, `id`, `attributes` (label, description, placeholder, options), `validations` (required)

### Shared Fields

All templates include:
- **Service / Repository** (input, required)
- **Priority** (dropdown, required): critical / high / medium / low
- **Area** (dropdown, required): frontend / backend / infrastructure / data / integrations
- **AI Delegation Candidate** (dropdown, optional): yes / maybe / no

### Template-Specific Fields

| Template | Required Fields |
|---|---|
| bug-report.yml | Bug Description, Steps to Reproduce, Expected Behavior, Actual Behavior |
| feature-request.yml | Problem Statement, Proposed Solution, Acceptance Criteria |
| tech-debt.yml | Current State, Desired State, Impact of Not Addressing |
| operational-issue.yml | Severity, Issue Description, Impact |

### Template Rules

- Dropdown options for Priority and Area must match `labels.yml`
- Every template auto-applies `type/*` and `status/triage` labels
- Keep `id` values stable (referenced by automations)
- `config.yml` disables blank issues and provides contact links

## Labels (labels.yml)

Canonical label taxonomy for all RentSpree repos, synced via github-label-sync.

### Categories

| Prefix | Purpose |
|---|---|
| `priority/` | Urgency: critical, high, medium, low |
| `type/` | Classification: bug, feature, tech-debt, operational |
| `area/` | System area: frontend, backend, infrastructure, data, integrations |
| `severity/` | Operational impact: critical, high, medium, low |
| `status/` | Workflow: triage, accepted, in-progress, blocked, wont-fix |
| `bot/` | Automation: md-drift, summary, md-first-gen |
| `ai-` | AI delegation: ai-candidate, ai-assigned |

### Format

```yaml
- name: "category/label-name"
  color: "hex-without-hash"
  description: "Short description"
```

### Rules

- Names are lowercase, `/` as category separator
- Colors are 6-character hex (no `#` prefix)
- New labels must also be added to template dropdowns if applicable

## Conventions

- All changes require PR review by `@rentspree/devex-team` and `@rentspree/infra-team`
- Files here act as [community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) defaults for the entire org
- Keep YAML valid and well-commented
- Template dropdown options should mirror `labels.yml` values

## Reference

- [ADR-0013: Adopt GitHub Issues for Project Issue Tracking](https://github.com/rentspree/rentspree-architecture/blob/main/adr/0013-adopt-github-issues-for-project-issue-tracking.md)
