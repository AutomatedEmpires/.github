# .github — AutomatedEmpires org operating system

This repo defines the reusable workflows, templates, and baseline agent contract for all AutomatedEmpires ventures.

## Doctrine

**Notion decides and builds. GitHub reviews and ships. Figma shows. Everything else runs.**

GitHub's job is implementation proof: code, checks, review, release history, and auditable agent routing.

## Reusable CI

Add a thin caller in a consuming repo at `.github/workflows/ci.yml`:

```yaml
name: CI

on:
  pull_request:
  merge_group:
  push:
    branches: [main]

concurrency:
  group: $ github.workflow -$ github.ref 
  cancel-in-progress: true

jobs:
  ci:
    uses: AutomatedEmpires/.github/.github/workflows/reusable-ci.yml@main
    secrets: inherit
```

## Agent-routing workflows

Active generic router commands:

- `@copilot` — apply Copilot review labels / human-authored Copilot trigger path.
- `@sentry` or `/review sentry <prompt>` — dispatch Sentry release-risk review if configured.
- `/git-agent <prompt>` or `/agent git <prompt>` — dispatch deterministic git-worker help if configured.

Important retirements / boundaries:

- Codex is retired org-wide as of 2026-06-06.
- Claude is handled by dedicated Claude workflows in repos that install them; the generic router does not dispatch Claude to avoid double-triggering.
- Routers only label, acknowledge, and dispatch. They never merge, deploy, checkout, or mutate product code.

## Inherited automatically

Issue templates, PR template, CODEOWNERS, SECURITY, CONTRIBUTING, SUPPORT, and FUNDING apply to repos that do not define their own copies.

## Per-repo, not inheritable

- Workflow files must be copied or called from each repo.
- Dependabot config is not org-inheritable. Use the shared Renovate preset: `{ "extends": ["github>AutomatedEmpires/.github"] }`.
- Product-specific guardrails stay in-repo unless promoted into a reusable workflow.

## Rollout standard

A venture is rollout-complete only when AGENTS, CI, routing, runtime pins, security posture, and Notion/GitHub alignment all match the org contract or have an explicit dated exception.
