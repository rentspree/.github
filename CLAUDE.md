# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Quick Reference

This is a configuration-only repository (no build/lint/test commands). It serves as the **organization-level defaults** for all RentSpree GitHub repositories, providing issue templates, label taxonomy, contributing guidelines, and code ownership.

## Repository Structure

```
.github/
  ISSUE_TEMPLATE/
    bug-report.yml           # Bug report issue form
    feature-request.yml      # Feature request issue form
    tech-debt.yml            # Tech debt issue form
    operational-issue.yml    # Operational/infrastructure issue form
    config.yml               # Issue template chooser config
labels.yml                   # Canonical label taxonomy for all repos
CODEOWNERS                   # Org-level code owners
CONTRIBUTING.md              # Contributing guidelines
README.md                    # Repo overview
```

## Working with Issue Templates

Issue templates use [GitHub Issue Forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues/syntax-for-issue-forms) (YAML-based forms, not legacy Markdown templates).

### Template Structure

Each template YAML file has:
- **Top-level fields**: `name`, `description`, `labels` (auto-applied on creation)
- **`body`**: Array of form elements (`markdown`, `input`, `textarea`, `dropdown`)
- **Each element**: `type`, `id` (unique identifier), `attributes` (label, description, placeholder, options), `validations` (required: true/false)

### Common Fields Across All Templates

All four templates include these shared fields:
- **Service / Repository** (`input`, required) -- identifies the affected repo
- **Priority** (`dropdown`, required) -- critical / high / medium / low
- **Area** (`dropdown`, required) -- frontend / backend / infrastructure / data / integrations
- **AI Delegation Candidate** (`dropdown`, optional) -- yes / maybe / no

### Template-Specific Required Fields

| Template | Key Required Fields |
|---|---|
| bug-report.yml | Bug Description, Steps to Reproduce, Expected Behavior, Actual Behavior |
| feature-request.yml | Problem Statement, Proposed Solution, Acceptance Criteria |
| tech-debt.yml | Current State, Desired State, Impact of Not Addressing |
| operational-issue.yml | Severity, Issue Description, Impact |

### Config (config.yml)

- `blank_issues_enabled: false` -- forces use of templates
- `contact_links` -- directs users to Slack (`#engineering`) and the Engineering Wiki before filing

### When Modifying Templates

1. Dropdown options for **Priority** and **Area** must stay aligned with the labels in `labels.yml`
2. Every template auto-applies `type/*` and `status/triage` labels
3. Keep `id` values stable -- they are referenced by automations and API consumers
4. Validate YAML syntax; malformed files silently break the issue chooser

## Working with labels.yml

`labels.yml` defines the canonical label taxonomy synced across all RentSpree repos (via github-label-sync or similar tooling).

### Label Categories

| Prefix | Purpose | Examples |
|---|---|---|
| `priority/` | Urgency level | critical, high, medium, low |
| `type/` | Issue classification | bug, feature, tech-debt, operational |
| `area/` | System area | frontend, backend, infrastructure, data, integrations |
| `severity/` | Operational impact | critical, high, medium, low |
| `status/` | Workflow state | triage, accepted, in-progress, blocked, wont-fix |
| `bot/` | Automation markers | md-drift, summary, md-first-gen |
| `ai-` | AI delegation | ai-candidate, ai-assigned |

### Label Entry Format

```yaml
- name: "category/label-name"
  color: "hex-without-hash"
  description: "Short description"
```

### When Modifying Labels

1. Keep names lowercase with `/` as category separator
2. Colors are 6-character hex strings (no `#` prefix)
3. Adding a new label here does not auto-sync -- repos must run the sync tool
4. If adding a new label that appears in issue template dropdowns, update the corresponding template YAML files too

## Repository Conventions

- All changes require PR review by `@rentspree/devex-team` and `@rentspree/infra-team` (per CODEOWNERS)
- This repo uses GitHub's [community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) convention -- files here serve as defaults for all org repos that don't define their own
- Keep template YAML validated and well-commented
- Dropdown options in templates should mirror `labels.yml` values where applicable

## Related Resources

- **ADR-0013**: [Adopt GitHub Issues for Project Issue Tracking](https://github.com/rentspree/rentspree-architecture/blob/main/adr/0013-adopt-github-issues-for-project-issue-tracking.md) -- the architectural decision record governing this setup
- **Engineering Wiki**: https://rentspree.github.io/rentspree-architecture/
