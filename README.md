# .github — AutomatedEmpires org config

This repo broadcasts org-wide defaults to every AutomatedEmpires repository.

## Reusable workflows (call from any repo)

Add a thin caller in the consuming repo at `.github/workflows/ci.yml`:

		name: CI
		on:
			pull_request:
			merge_group:
			push:
				branches: [main]
		jobs:
			ci:
				uses: AutomatedEmpires/.github/.github/workflows/reusable-ci.yml@main
				secrets: inherit

## Inherited automatically

Issue templates, PR template, CODEOWNERS, and SECURITY/CONTRIBUTING/SUPPORT/FUNDING
apply to any repo that does not define its own copy.

## Per-repo (not inheritable)

- Dependabot config is not org-inheritable — use the shared Renovate preset:
	consumers add `{ "extends": ["github>AutomatedEmpires/.github"] }`.
- Repo-specific CI jobs (e.g. E&E's G22 Verified-Host guardrail) stay in-repo.