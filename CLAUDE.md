# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Quick Reference

This is a configuration-only repository (no build/lint/test commands). It provides **organization-level GitHub defaults** for all repositories in this org.

## Repository Structure

```
.github/
  ISSUE_TEMPLATE/
    bug-report.yml           # Bug report issue form
    feature-request.yml      # Feature request issue form
    tech-debt.yml            # Tech debt issue form
    operational-issue.yml    # Operational/infrastructure issue form
    config.yml               # Issue template chooser config
CODEOWNERS                   # Org-level code owners
CONTRIBUTING.md              # Contributing guidelines
README.md                    # Repo overview
```

## Working with Issue Templates

Templates use [GitHub Issue Forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms) YAML syntax.

### Template Structure

Each `.yml` template has:
- **Top-level fields**: `name`, `description`, `labels` (auto-applied on creation)
- **`body`**: Array of form elements (`markdown`, `input`, `textarea`, `dropdown`)
- **Each element**: `type`, `id`, `attributes` (label, description, placeholder, options), `validations` (required)

### Shared Fields Across All Templates

- **Service / Repository** (input, required)
- **Priority** (dropdown, required): critical / high / medium / low
- **Area** (dropdown, required): frontend / backend / infrastructure / data / integrations
- **AI Delegation Candidate** (dropdown, optional): yes / maybe / no

### When Modifying Templates

1. Dropdown options for Priority and Area must stay aligned with the canonical label taxonomy
2. Every template auto-applies `type/*` and `status/triage` labels
3. Keep `id` values stable — they may be referenced by automations
4. Validate YAML syntax; malformed files silently break the issue chooser

## Repository Conventions

- This repo is **public** — do not add internal URLs, secrets, or sensitive information
- Files here act as [community health file](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) defaults for the entire org
- Repos that define their own `.github/ISSUE_TEMPLATE/` override these defaults
- Keep YAML validated and well-commented
- The canonical label taxonomy and sync workflow live in a private repo
