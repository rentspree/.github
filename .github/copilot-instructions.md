# Copilot Instructions

This file provides guidance to GitHub Copilot when working with code in this repository.

## Repository Overview

This is a **configuration-only repository** (no build, lint, or test commands). It provides **organization-level GitHub defaults** for all repositories in this org:

- **Issue form templates** (`.github/ISSUE_TEMPLATE/`) — YAML-based forms for bug reports, feature requests, tech debt, and operational issues
- **Label taxonomy** (`labels.yml`) — canonical labels for all repos
- **Contributing guidelines** (`CONTRIBUTING.md`) and **code ownership** (`CODEOWNERS`)

## Issue Templates

Templates use [GitHub Issue Forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms) YAML syntax.

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

### Template Rules

- Dropdown options for Priority and Area must match `labels.yml`
- Every template auto-applies `type/*` and `status/triage` labels
- Keep `id` values stable (may be referenced by automations)
- `config.yml` disables blank issues and provides contact links

## Labels (labels.yml)

### Label Format

```yaml
- name: "category/label-name"
  color: "hex-without-hash"
  description: "Short description"
```

### Rules

- Names are lowercase, `/` as category separator
- Colors are 6-character hex (no `#` prefix)
- New labels must also be added to template dropdowns if applicable
- After modifying `labels.yml`, org default labels must be updated via the GitHub org settings UI at `https://github.com/organizations/rentspree/settings/repository-defaults` (no API exists for org-level default labels)

## Conventions

- This repo is **public** — do not add internal URLs, secrets, or sensitive information
- Files here act as [community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) defaults for the entire org
- Keep YAML valid and well-commented
