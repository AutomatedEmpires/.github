# AutomatedEmpires — Agent Operating Manual

This file sets the baseline rules for every AI agent working in this org.
Repo-level AGENTS.md files may extend, but not loosen, these rules.

## Stack (the golden path)

- TypeScript, Next.js (App Router), Turborepo
- Supabase Postgres (+PostGIS), Clerk auth, Supabase RLS keyed on Clerk `sub`
- Mapbox (production maps), Stripe (+Connect where needed)
- Vercel (deploy), Doppler (secrets), PostHog (analytics/flags), Sentry (errors)
- Single icon system only (shared registry) — no lucide/heroicons/react-icons/fontawesome/mui-icons

## Runtime (pin everywhere)

- Node 24.16.0 · pnpm 10.12.4
- Commit lockfiles. CI installs with --frozen-lockfile.

## How work is routed

- File a build task as a GitHub Issue titled `[build] ...` using the Build Task template.
- Fill `## Area`, `## Suggested agent`, `## Risk level` with one allowed label each.
- The agent-build-task-router applies labels automatically.
- On PRs, trigger agents via comment: `@claude`, `@sentry`, `@copilot`,
  or `/agent <name> <prompt>`, `/review <name>`, `/git-agent <prompt>`.
- Only OWNER/MEMBER/COLLABORATOR comments are honored.

## Risk lanes

- risk:low — agents may open PRs autonomously; CI gates merge.
- risk:medium — agent drafts, human reviews before merge.
- risk:high / risk:approval-required — human approval required before any code change.

## Hard rules

- Never weaken RLS or expose secrets in code or logs.
- Never merge with red CI. Never bypass branch protection.
- Database migrations follow expand/contract; never additive + destructive in one release.
- Routers never merge, deploy, checkout, or mutate code.